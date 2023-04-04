<script setup>
import { ref } from 'vue';
const results_display = ref({ value: '' });
function handleDrop( e ) {
  
  const f = e.dataTransfer.files[ 0 ];
  /* f is a File */
  const reader = new FileReader();
  reader.onload = function( e ) {
    const data = e.target.result;

    /* reader.readAsArrayBuffer(file) -> data will be an ArrayBuffer */
    const wb = XLSX.read( data ),
      wsName = wb.SheetNames[ 0 ],
      ws = wb.Sheets[ wsName ];

    /* sheetData turns column headers into keys */
    const sheetData = XLSX.utils.sheet_to_json( ws );
    let strDisplay = '# of total data rows: ' + sheetData.length;


    /* panel_column needs to be computed as the integer representing the 'panel' column found */
    const panel_column = getPanelColumnNumber( ws );

    if ( panel_column === -1 ) {
      strDisplay = strDisplay + ' ' + 'NO PANEL COLUMN';
    } else {
      /* process panel count and create new workbook to download results */
      const arrVals = xlsxCountColumnVals( ws, parseInt( panel_column ) );
      strDisplay = strDisplay + ' ' + JSON.stringify( arrVals );
    }

    /* display results to user */
    results_display.value.value = strDisplay;

  };
  reader.readAsArrayBuffer( f );
}

/**
 * function getPanelColumnNumber( ws )
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
/**
 * function xlsxCountColumnVals( ws, column )
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
              val = ( removeBadCharacters( ws[ cell_ref ].v) );
              arrCounts[ val ] = arrCounts[ val ] + 1;  // add 1 for the value found in this row of the column
          }
      }	
  } catch ( err ) {
      next ( err );
  }
  return arrCounts;
}
/**
 * function getUniqueValues( ws, column )
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
/**
* function union( setA, setB )
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
</script>
<template>
  <div class="tool">
    <div class="flex-column">
      <div class="column-item">
        <img alt="EMR Report" src="@/assets/cyclone.svg" width="90" height="90" />
      </div>
      <div class="column-item">
        <h1>Panel Count</h1>
      </div>
    </div>
  <h2>Analyze File for Panel Count</h2>

  <p>There must be a 'panel' column in the XLSX file dropped into the box below:</p>
  
  <div @dragover.prevent
      @drop="handleDrop"
      id="drop_dom_element">Drop .xlsx file here to initiate panel count</div>

  <br>

  <div id="results_display">{{ results_display.value }}</div>

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
  width: 271px;
  padding: 4px;
  border-color: black;
  border-style:double;
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