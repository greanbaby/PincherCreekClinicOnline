<script setup>
/** PhysicianView.vue
 * 
 * This page currently loops through the physicians and displays their picture
 * 
 * FUTURE DEVELOPMENT will turn these into 'executive summary' pages
 * 
 * 
 * @author Scott Gingras March 30, 2023
 * 
 * TODO: Add TAB navigation to browse executive summaries for physicians
 * 
 * ---------------------------------------------
 * HTML TEMPLATE CODE TO HIDE PHYSICIANS BY BUTTON HAS BEEN COMMENTED OUT BELOW:
    <!-- Toggle Show Physicians -->
    <!-- <button @click="toggleShowPhysicians">
    <span v-show="showPhysicians">Hide Physicians</span>
    <span v-show="!showPhysicians">Show Physicians</span>
    </button> -->
 * ---------------------------------------------
 */
defineProps(['physicians'])
</script>
<template>
  <div class="physician">
   
    <div class="doctorsdisplay flex-column">
      <div v-for="doc in physicians" :key="doc" class="doc column-item">
        
        <img 
          v-bind:src="doc.img" 
          v-bind:alt="doc.name"
          class="small_image_display"><br>
        {{ doc.name }}<br>
        
        {{ doc.panelsize.toLocaleString() }} patients<br>

        <small>{{ (doc.overage49/doc.panelsize).toLocaleString(undefined,{style: 'percent', minimumFractionDigits:1}) }} age 50+
          </small><br>

        <small>{{ (doc.females/doc.panelsize).toLocaleString(undefined,{style: 'percent', minimumFractionDigits:1}) }} female
          </small><br>

        {{ doc.complexity }} complexity<br>

        <small>{{ (doc.localresident/doc.panelsize).toLocaleString(undefined,{style: 'percent', minimumFractionDigits:1}) }} local residents
          </small><br>

        <small>{{ (doc.seeninpast2yrs/doc.panelsize).toLocaleString(undefined,{style: 'percent', minimumFractionDigits:1}) }} seen in past 2yrs
          </small><br>

        {{ (doc.emailonfile/doc.panelsize).toLocaleString(undefined,{style: 'percent', minimumFractionDigits:1}) }} have email
          <br>

        <small>{{ (doc.affiliated/doc.panelsize).toLocaleString(undefined,{style: 'percent', minimumFractionDigits:1}) }} affiliated (BCM)
          </small><br>

        {{ doc.noshowrate }}% no shows<br>

        <strong>{{ doc.over2noshows }}</strong> patients <small>with more than 2 no shows this year</small>
        
      </div>
    </div>
  </div>

</template>
<style scoped>
.flex-column {
  margin-top: 10px;
  display: grid;
}
  .flex-column {
  margin-top: 10px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 15px;
}
.column-item {
  border: 1px dotted hsla(160, 100%, 37%, 0.5);
}
div.doctorsdisplay {
  margin-top: 4px;
  text-align: center;
}
div.physician {
  margin-top: 4px;
  text-align: center;
}
div.doc {
  margin: 8px;
}
img.small_image_display {
  height: 96px;
  padding: 5px;
}
@media (min-width: 1024px) {
  .physician {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>