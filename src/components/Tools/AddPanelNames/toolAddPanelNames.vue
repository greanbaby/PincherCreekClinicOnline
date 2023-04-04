<script setup>
import { ref } from 'vue';
const results_display = ref({ value: '' });
const results_display2 = ref({ value: '' });
/* globals wb and ws containing file_one workbook and worksheet */
var wb;
var ws;
var range;
var lastColOne;
/* FILE ONE HANDLER */
function handleDrop( e ) {
  const f = e.dataTransfer.files[ 0 ];
  /* f is a File */
  const reader = new FileReader();
  reader.onload = function( e ) {
    const data = e.target.result;

    // wb is global
    wb = XLSX.read( data );

    /* reader.readAsArrayBuffer(file) -> data will be an ArrayBuffer */
    const wsName = wb.SheetNames[ 0 ];

    ws = wb.Sheets[ wsName ];
    range = XLSX.utils.decode_range( ws[ '!ref' ] );
    lastColOne = range.e.c;

    /* sheetData turns column headers into keys */
    const sheetData = XLSX.utils.sheet_to_json( ws );
    let strDisplay = '# data rows: ' + sheetData.length;

    /* display results to user */
    results_display.value.value = strDisplay;

  };
  reader.readAsArrayBuffer( f );
}

/* FILE TWO HANDLER */
function handleDrop2( e ) {
  
  const f = e.dataTransfer.files[ 0 ];
  /* f is a File */
  const reader = new FileReader();
  reader.onload = function( e ) {
    const data = e.target.result;

    /* reader.readAsArrayBuffer(file) -> data will be an ArrayBuffer */
    const wb2 = XLSX.read( data ),
      wsName2 = wb2.SheetNames[ 0 ],
      ws2 = wb2.Sheets[ wsName2 ];

    /* sheetData turns column headers into keys */
    const sheetData2 = XLSX.utils.sheet_to_json( ws2 );
    let strDisplay2 = '# data rows: ' + sheetData2.length;

    /* display results to user */
    results_display2.value.value = strDisplay2;

    /* generate new workbook with only rows from file1 matching file2 by the last columns */
    const newWorkBook = newWB( "Matches" );

    const range2 = XLSX.utils.decode_range( ws2[ '!ref' ] );
    const lastColTwo = range2.e.c;

    // prepare data as Array of Arrays
    const ws_data = fncGetArrayOfPanelsAddedFromRowsMatching( ws, lastColOne, ws2, lastColTwo );

    // prepare results sheet with data
    newWorkBook.SheetNames.push( 'results' );
    const wsn = XLSX.utils.aoa_to_sheet( ws_data );  // A rray  O f  A rray _to_ Sheet
    newWorkBook.Sheets[ 'results' ] = wsn;

    // save workbook
    const write_opts = {};
    XLSX.writeFile( newWorkBook, "Matches.xlsx", { compression: true } );

  };
  reader.readAsArrayBuffer( f );
}
/** function newWB
 * @returns newly created xlsx workbook object
 */
function newWB( strTitle ) {
  let wb = XLSX.utils.book_new();
  wb.Props = {
      Title: strTitle,
      Author: "Scott Gingras"
  };
  return wb;
}
/** function getPanelColumnNumber( ws )
 * @param ws is the worksheet object
 * @returns number representing the column containing 'panel' as the header
 */
function getPanelColumnNumber( ws ) {
  const range = XLSX.utils.decode_range( ws[ '!ref' ] );
  const R = range.s.r;
  for ( let C = 0; C <= range.e.c; ++C ) {
    let cell_address = { c:C, r:R },
      cell_ref = XLSX.utils.encode_cell( cell_address ),
      val = '';
    if ( typeof( ws[ cell_ref ]) !== 'undefined' ) {
      val = ( removeBadCharacters( ws[ cell_ref ].v) );
      if ( val.toLowerCase() === 'panel' ) {
        return C;
      }
    }
  }
  return -1;  // if we didn't find 'panel' then return -1
  
}
/** function xlsxCountColumnVals( ws, column )
 * @param ws is the worksheet object to process
 * @param column is the column to read and return count for
 * @returns array of counts of the values found in column
 */
function xlsxCountColumnVals( ws, column ) {
  let setVals = new Set(), // unique values in the column
      arrCounts = {}; // array containing count of occurrances for all of these unique values
  try {
      setVals = union( setVals, getUniqueValues( ws, column ) );  // unique set of nicely formatted values
      for ( let val of setVals ) {
          arrCounts[ val ] = 0;  // arrCounts contains all of the column's values now
      }
      const range = XLSX.utils.decode_range( ws[ '!ref' ] );  // go through entire worksheet
      for ( let R = range.s.r+1; R <= range.e.r; ++R ) {
          let cell_address = { c:column, r:R },
              cell_ref = XLSX.utils.encode_cell( cell_address ),  // get raw cell value
              val = '';
          if ( typeof( ws[ cell_ref ]) !== 'undefined' ) {
              val = ( removeBadCharacters( ws[ cell_ref ].v ) );
              arrCounts[ val ] = arrCounts[ val ] + 1;  // add 1 for the value found in this row of the column
          }
      }	
  } catch ( err ) {
      next ( err );
  }
  return arrCounts;
}
/** function getUniqueValues( ws, column )
 * @returns unique list of values found in column
 */
function getUniqueValues( ws, column ) {
  let setUniques = new Set();
  const range = XLSX.utils.decode_range( ws[ '!ref' ] );
  for ( let R = range.s.r+1; R <= range.e.r; ++R ) {
      const cell_address = { c:column, r:R },
          cell_ref = XLSX.utils.encode_cell( cell_address );
      if ( typeof( ws[ cell_ref ]) !== 'undefined' ) {
          setUniques.add( removeBadCharacters( ws[ cell_ref ].v) );
      }
  }	
  return setUniques;
}
/** function union( setA, setB )
* @param setA is the first set object to join
* @param setB is the second set object to join
* @returns union of the 2 sets given as parameters
*/
function union( setA, setB ) {
  let _union = new Set( setA );
  for ( let elem of setB ) {
      _union.add( elem );
  }
  return _union;
}
function removeBadCharacters( setVal ) {
  //  □  :  \  /  ?  *  [  ]
let validName = '';
if ( typeof( setVal ) !== 'string' ) {
  return '';
} else {
      validName = setVal.replace( "□", "" )
          .replace( ":", "" )
          .replace( "\\", "" )
          .replace( "/", "" )
          .replace( "[", "" )
          .replace( "]", "" );
}
return validName.trim();
}
/** function fncGetArrayOfRowsMatching
 *   - given 2 worksheets build a new array of values
 *     that are the rows from worksheet 1 that match worksheet 2, using file one/two
 *     options to specify the columns to use in the comparison.
 * @returns Array of Arrays which can be written into a workbook directly with aoa_to_sheet
 */
function fncGetArrayOfRowsMatching( ws1, file_one_options, ws2, file_two_options ) {
  const ws1Values = XLSX.utils.sheet_to_json( ws1, { header:1 } ),
      ws2Values = XLSX.utils.sheet_to_json( ws2, { header:1 } );

  // update global variables with count of # data rows for each file
  oneDataRows = ws1Values.length;
  twoDataRows = ws2Values.length;

  let datavalues = [[]];
  // loop through all rows of original file to compare
  for ( let x = 0; x < ws1Values.length; x++ ) {
      const rowOriginalFileToCompare = ws1Values[ x ];
      let valCompare = rowOriginalFileToCompare[ file_one_options ],
          boolMatching = false;

      // loop through all rows of second file used to look for matches
      for ( let y = 0; y < ws2Values.length; y++ ) {
          const rowFileTwoMatcher = ws2Values[ y ],
              valMatcher = rowFileTwoMatcher[ file_two_options ];

          if ( valCompare === valMatcher ) {
              boolMatching = true;
              break;
          }
      }
      if ( boolMatching ) {
          datavalues.push( rowOriginalFileToCompare );
      }
  }
  return datavalues;
}
/** function fncGetArrayOfPanelsAddedFromRowsMatching
 *   - given 2 worksheets build a new array of values
 *     that are the rows from worksheet 1 and copying the column value
 *     from the column previous to the one used to match if a match is found
 * @returns Array of Arrays which can be written into a workbook directly with aoa_to_sheet
 */
function fncGetArrayOfPanelsAddedFromRowsMatching( ws1, file_one_options, ws2, file_two_options ) {
  const ws1Values = XLSX.utils.sheet_to_json( ws1, { header:1 } ),
      ws2Values = XLSX.utils.sheet_to_json( ws2, { header:1 } );

  // update global variables with count of # data rows for each file
  oneDataRows = ws1Values.length;
  twoDataRows = ws2Values.length;

  let datavalues = [[]];
  // loop through all rows of original file to compare
  for ( let x = 0; x < ws1Values.length; x++ ) {
    
    const rowOriginalFileToCompare = ws1Values[ x ];
    let valCompare = rowOriginalFileToCompare[ file_one_options ],
        boolMatching = false,
        panelMatching = undefined;

    // loop through all rows of second file used to look for matches
    for ( let y = 0; y < ws2Values.length; y++ ) {
        const rowFileTwoMatcher = ws2Values[ y ],
            valMatcher = rowFileTwoMatcher[ file_two_options ];

        if ( valCompare === valMatcher ) {

            // capture the 2nd last column value now to write into the original sheet
            panelMatching = rowFileTwoMatcher[ file_two_options-1 ];

            boolMatching = true;
            break;
        }
    }
    if ( boolMatching ) {

      // add the 2nd last column value captured into rowOriginalFileToCompare at the end
      rowOriginalFileToCompare.push( panelMatching );

    }
    datavalues.push( rowOriginalFileToCompare );
}
return datavalues;
}
</script>
<template>
  <div class="tool">
    <div class="flex-column">
      <div class="column-item">
        <img alt="EMR Report" src="@/assets/fingerprint.svg" width="80" height="80" />
      </div>
      <div class="column-item">
        <h1>Copy Panels</h1>
      </div>
    </div>
    <h2>Copy Panel Names From File Two to File One</h2>

    <p>The last columns are used generate a new file with matches from file one looking up the panel name from the matching row</p>
    
    <div @dragover.prevent
      @drop="handleDrop"
      id="drop_dom_element">
        Drop .xlsx file here to initiate panel count</div>
    <br>

    <div id="results_display">{{ results_display.value.value }}</div>

    <div @dragover.prevent
      @drop="handleDrop2"
      id="drop_dom_element2">Drop file two here</div>
    <br>

    <div id="results_display2">{{ results_display2.value.value }}</div>

    <br>
  </div>
  
</template>
<style scoped>
.flex-column {
  margin-top: 10px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 15px;
}
/* grid-template-columns: 1fr 1fr; */
.column-item {
  padding: 0px;
  margin-top:10px;
}
.tool {
  border: 1px solid hsla(160, 100%, 37%, 0.5);
  margin-top: 0px;
  padding: 6px;
}
h1 {
  margin-top: 2px;
}
h2 {
  padding-left: 30px;
}
p {
  padding: 30px;
}

div#drop_dom_element {
  color: black;
  background-color: hsla(160, 100%, 37%, 0.5);
  width: 360px;
  padding: 24px;
  border-color: black;
  border-style:double;
  font-weight: bolder;
  margin-left: 30px;
}

div#drop_dom_element2 {
  color: rgb(55, 0, 255);
  background-color:  rgb(116, 231, 87);
  width: 360px;
  padding: 24px;
  border-color: black;
  border-style:double;
  font-weight: bolder;
  margin-left: 30px;
}

div#results_display {
  inherits:false;
  font-size: larger;
  font-stretch: wider;
  color: black;
}

div#results_display2 {
  font-size: larger;
  font-stretch: wider;
  color: black;
}
</style>