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
    <h1>Physician page currently under construction (Apr. 1, 2023)</h1>
    <div class="doctorsdisplay flex-column">
      <div v-for="doc in physicians" :key="doc" class="doc column-item">
        
        <img 
          v-bind:src="doc.img" 
          v-bind:alt="doc.name"
          class="small_image_display"><br>
        <small>{{ doc.name }}</small>
        
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
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 15px;
}

.column-item {
  border: 1px dotted hsla(160, 100%, 37%, 0.5);
}
div.doctorsdisplay {
  margin-top: 24px;
  text-align: center;
}
div.physician {
  margin-top: 24px;
  text-align: center;
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
