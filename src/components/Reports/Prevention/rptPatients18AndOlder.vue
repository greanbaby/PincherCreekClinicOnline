<script setup>
/** Patients Age 18+
 * 
 * Displayed at the bottom of the Prevention and Screening Report
 * 
 * This is a summary of the Adult Patients age 18+ for the whole clinic
 * 
 * @author Scott Gingras March 31, 2023
 */
defineProps([ 'repertoires' ])
</script>
<template>
  <div class="rptWrap2">
  <h2>Prevention and Screening Patients Age 18+</h2>
    <div class="flex-column">
      <div class="column-item" v-for="item in repertoires" :key="item">

        <h4>{{ item.time_period.toDateString() }}</h4>
        <!-- Touchstones -->
        <ul>
          <li v-for="touchstone in item.touchstones" :key="touchstone" class="homelist">
            {{ touchstone.physician }} {{ touchstone.BP_Denominator.toLocaleString() }}
          </li>
        </ul>
        <br>
      </div>
    </div>
  </div>
</template>
<style scoped>
@media (min-width: 1024px) {
  .rptWrap2 {
    min-height: 100vh;
    align-items: center;
  }
}
.flex-column {
  margin-top: 1px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 15px;
}
.column-item {
  padding: 0px;
  margin-top:10px;
}
</style>
