<script setup>
/** No Shows
 * 
 * No Shows Report which allows the user to select the date
 * 
 * @Author Scott Gingras April 20, 2023
 */
import { reactive, computed } from 'vue';

const datechosen = reactive({ datevalue: 'Thu Apr 20 2023' });

const myProps = defineProps([ 'noshows' ]);

const chosenNoShows = computed(() => {
  let singleDate = myProps.noshows.filter(item => item.time_period.toDateString() === datechosen.datevalue);
  let singleDateTouchstones = singleDate[0].touchstones;
  return singleDateTouchstones;
});

</script>
<template>
  <div class="rptWrap">
    <div class="flex-column">
      <div class="column-item">
        <h3>No Shows for Attending Providers</h3>
        <img alt="Alarm" src="@/assets/alarm-clock.svg" width="100" height="100" />
      </div>
      <div class="column-item">
        
        <p class="no-print">CHOOSE DATE:<br>

        <select v-model="datechosen.datevalue">
          <option disabled value="">Please select one</option>
          <option v-for="item in noshows" :key="item">
            {{ item.time_period.toDateString() }}
          </option>
        </select>

        </p>
      </div>
    </div>

    <table>
      <caption>Number of No Shows counted on {{ datechosen.datevalue }}</caption>
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
        <tr v-for="touchstone in chosenNoShows" :key="touchstone.provider">
          <td>{{ touchstone.provider }}</td>
          <td>{{ touchstone.noshows_1month.toLocaleString() }}</td>
          <td>{{ touchstone.noshows_3month.toLocaleString() }}</td>
          <td>{{ touchstone.noshows_6month.toLocaleString() }}</td>
          <td>{{ touchstone.noshows_12month.toLocaleString() }}</td>
        </tr>
      </tbody>
    </table>

  </div>

</template>
<style scoped>

</style>