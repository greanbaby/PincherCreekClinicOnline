<script setup>
/** Visits
 * 
 * Visits Report which allows the user to select the date
 * 
 * @Author Scott Gingras May 5, 2023
 */
import { reactive, computed } from 'vue';

const datechosen = reactive({ datevalue: 'Tue Apr 25 2023' });

const myProps = defineProps([ 'visits' ]);

const chosenVisits = computed(() => {
  let singleDate = myProps.visits.filter(item => item.time_period.toDateString() === datechosen.datevalue);
  let singleDateTouchstones = singleDate[0].touchstones;
  return singleDateTouchstones;
});

</script>
<template>
  <div class="rptWrap">
    <div class="flex-column">
      <div class="column-item">
        <h3>Visits for Attending Providers</h3>
        <img alt="Visits" src="@/assets/help-others.svg" width="100" height="100" />
      </div>
      <div class="column-item">
        
        <p class="no-print">CHOOSE DATE:<br>

        <select v-model="datechosen.datevalue">
          <option disabled value="">Please select one</option>
          <option v-for="item in visits" :key="item">
            {{ item.time_period.toDateString() }}
          </option>
        </select>

        </p>
      </div>
    </div>

    <table>
      <caption>Number of Visits counted on {{ datechosen.datevalue }}</caption>
      <thead>
        <tr>
          <th>Attending Provider</th>
          <th>1 Month</th>
          <th>3 Months</th>
          <th>6 Months</th>
          <th>12 Months</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="touchstone in chosenVisits" :key="touchstone.provider">
          <td>{{ touchstone.provider }}</td>
          <td>{{ touchstone.visits_1month.toLocaleString() }}</td>
          <td>{{ touchstone.visits_3month.toLocaleString() }}</td>
          <td>{{ touchstone.visits_6month.toLocaleString() }}</td>
          <td>{{ touchstone.visits_12month.toLocaleString() }}</td>
        </tr>
      </tbody>
    </table>

  </div>

</template>
<style scoped>

</style>