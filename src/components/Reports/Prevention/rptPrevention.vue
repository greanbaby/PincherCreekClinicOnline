<script setup>
/** Prevention
 * 
 * Prevention and Screening Report which allows the user to select the date
 * and select the physician to view.
 * 
 * It includes a graph for the selected data.
 * 
 * It also includes a summary of the Adult Patients age 18+ for the whole clinic at the bottom
 * 
 * @author Scott Gingras March 31, 2023
 */
import ReportGraph from '/src/components/Reports/Prevention/rptGraphPreventions.vue';
import ReportAdults from '/src/components/Reports/Prevention/rptPatients18AndOlder.vue';

import { reactive, computed } from 'vue';

const datechosen = reactive({ datevalue: 'Mon Apr 10 2023' });
const docchosen = reactive({ docvalue: 'TOTAL' });

const myProps = defineProps([ 'repertoires', 'physicians' ]);

/**
 * chosenReportDetails COMPUTED VALUE
 * Will contain only the touchstones to be displayed for the selected year and physician
 */
const chosenReportDetails = computed(() => {
  let singleDate = myProps.repertoires.filter(item => item.time_period.toDateString() === datechosen.datevalue);
  let singleDateTouchstones = singleDate[0].touchstones;
  let singleDoc = singleDateTouchstones.filter(item => item.physician === docchosen.docvalue);
  return singleDoc[0];
});

/**
 * chosenReportTotals COMPUTED VALUE
 * Will contain the touchstones to be displayed for the selected year for TOTAL
 */
 const chosenReportTotals = computed(() => {
  let singleDate = myProps.repertoires.filter(item => item.time_period.toDateString() === datechosen.datevalue);
  let singleDateTouchstones = singleDate[0].touchstones;
  let totalDoc = singleDateTouchstones.filter(item => item.physician === 'TOTAL');
  return totalDoc[0];
});


</script>
<template>
  <div class="rptWrap">
    <div class="flex-column">
      <div class="column-item">
        <img alt="EMR Report" src="@/assets/statistics.svg" width="100" height="100" />
      </div>
      <div class="column-item">
        <p>CHOOSE DATE:<br>

          <select v-model="datechosen.datevalue">
            <option disabled value="">Please select one</option>
            <option v-for="item in repertoires" :key="item">
              {{ item.time_period.toDateString() }}
            </option>
          </select>

        </p>
        <p>CHOOSE PHYSICIAN:<br>
        
        <select v-model="docchosen.docvalue">
          <option disabled value="">Please select one</option>
          <option v-for="doc in physicians" :key="doc">
            {{ doc.name }}
          </option>
        </select>

      </p>
      </div>
      <div class="column-item">
        
      </div>
    </div>

    
    <table>
      <caption>{{ docchosen.docvalue }} ({{ datechosen.datevalue }})</caption>
      <thead>
        <tr>
          <th scope="col">Category</th>
          <th scope="col">Dividend</th>
          <th scope="col">Divisor</th>
          <th scope="col" class="strongly">%</th>
          <th scope="col" v-if="docchosen.docvalue!=='TOTAL'">Clinic Average</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">Blood Pressure</th>
          <td>{{ chosenReportDetails.BP_Numerator.toLocaleString() }}</td>
          <td>{{ chosenReportDetails.BP_Denominator.toLocaleString() }}</td>
          <td class="strongly">{{ ((chosenReportDetails.BP_Numerator / chosenReportDetails.BP_Denominator) * 100).toFixed( 1 ) }}%</td>
          <td v-if="docchosen.docvalue!=='TOTAL'">{{ ((chosenReportTotals.BP_Numerator / chosenReportTotals.BP_Denominator) * 100).toFixed( 1 ) }}%</td>
        </tr>

        <tr>
          <th scope="row">Colorectal Cancer Screen</th>
          <td>{{ chosenReportDetails.CRC_Numerator.toLocaleString() }}</td>
          <td>{{ chosenReportDetails.CRC_Denominator.toLocaleString() }}</td>
          <td class="strongly">{{ ((chosenReportDetails.CRC_Numerator / chosenReportDetails.CRC_Denominator) * 100).toFixed( 1 ) }}%</td>
          <td v-if="docchosen.docvalue!=='TOTAL'">{{ ((chosenReportTotals.CRC_Numerator / chosenReportTotals.CRC_Denominator) * 100).toFixed( 1 ) }}%</td>
        </tr>

        <tr>
          <th scope="row">Exercise Assessment</th>
          <td>{{ chosenReportDetails.Exercise_Numerator.toLocaleString() }}</td>
          <td>{{ chosenReportDetails.Exercise_Denominator.toLocaleString() }}</td>
          <td class="strongly">{{ ((chosenReportDetails.Exercise_Numerator / chosenReportDetails.Exercise_Denominator) * 100).toFixed( 1 ) }}%</td>
          <td v-if="docchosen.docvalue!=='TOTAL'">{{ ((chosenReportTotals.Exercise_Numerator / chosenReportTotals.Exercise_Denominator) * 100).toFixed( 1 ) }}%</td>
        </tr>

        <tr>
          <th scope="row">Height</th>
          <td>{{ chosenReportDetails.Height_Numerator.toLocaleString() }}</td>
          <td>{{ chosenReportDetails.Height_Denominator.toLocaleString() }}</td>
          <td class="strongly">{{ ((chosenReportDetails.Height_Numerator / chosenReportDetails.Height_Denominator) * 100).toFixed( 1 ) }}%</td>
          <td v-if="docchosen.docvalue!=='TOTAL'">{{ ((chosenReportTotals.Height_Numerator / chosenReportTotals.Height_Denominator) * 100).toFixed( 1 ) }}%</td>
        </tr>

        <tr>
          <th scope="row">Mammography</th>
          <td>{{ chosenReportDetails.Mammo_Numerator.toLocaleString() }}</td>
          <td>{{ chosenReportDetails.Mammo_Denominator.toLocaleString() }}</td>
          <td class="strongly">{{ ((chosenReportDetails.Mammo_Numerator / chosenReportDetails.Mammo_Denominator) * 100).toFixed( 1 ) }}%</td>
          <td v-if="docchosen.docvalue!=='TOTAL'">{{ ((chosenReportTotals.Mammo_Numerator / chosenReportTotals.Mammo_Denominator) * 100).toFixed( 1 ) }}%</td>
        </tr>

        <tr>
          <th scope="row">Pap Test</th>
          <td>{{ chosenReportDetails.Pap_Numerator.toLocaleString() }}</td>
          <td>{{ chosenReportDetails.Pap_Denominator.toLocaleString() }}</td>
          <td class="strongly">{{ ((chosenReportDetails.Pap_Numerator / chosenReportDetails.Pap_Denominator) * 100).toFixed( 1 ) }}%</td>
          <td v-if="docchosen.docvalue!=='TOTAL'">{{ ((chosenReportTotals.Pap_Numerator / chosenReportTotals.Pap_Denominator) * 100).toFixed( 1 ) }}%</td>
        </tr>

        <tr>
          <th scope="row">Tobacco Use Assessment</th>
          <td>{{ chosenReportDetails.Smoking_Numerator.toLocaleString() }}</td>
          <td>{{ chosenReportDetails.Smoking_Denominator.toLocaleString() }}</td>
          <td class="strongly">{{ ((chosenReportDetails.Smoking_Numerator / chosenReportDetails.Smoking_Denominator) * 100).toFixed( 1 ) }}%</td>
          <td v-if="docchosen.docvalue!=='TOTAL'">{{ ((chosenReportTotals.Smoking_Numerator / chosenReportTotals.Smoking_Denominator) * 100).toFixed( 1 ) }}%</td>
        </tr>

        <tr>
          <th scope="row">Weight</th>
          <td>{{ chosenReportDetails.Weight_Numerator.toLocaleString() }}</td>
          <td>{{ chosenReportDetails.Weight_Denominator.toLocaleString() }}</td>
          <td class="strongly">{{ ((chosenReportDetails.Weight_Numerator / chosenReportDetails.Weight_Denominator) * 100).toFixed( 1 ) }}%</td>
          <td v-if="docchosen.docvalue!=='TOTAL'">{{ ((chosenReportTotals.Weight_Numerator / chosenReportTotals.Weight_Denominator) * 100).toFixed( 1 ) }}%</td>
        </tr>

      </tbody>
      <!-- <tfoot>
        <tr>
          <th scope="row" colspan="2">{{ docchosen.docvalue }}</th>
          <td colspan="2">{{ datechosen.datevalue }}</td>
        </tr>
      </tfoot> -->
    </table>

  </div>

  <ReportGraph :chosenReportDetails=chosenReportDetails :chosenReportTotals=chosenReportTotals />
  <br>
  <ReportAdults :repertoires=repertoires />
  
</template>
<style scoped>

</style>
