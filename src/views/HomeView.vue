<script setup>
/** HomeView.vue
 * 
 * The home page contains a loop through all the physicians to display their image
 * 
 * @author Scott Gingras March 30, 2023
 */
import TheWelcome from '../components/TheWelcome.vue'
defineProps(['physicians'])
</script>
<template>
  <main>
    <TheWelcome />
    <div class="doctorsdisplay">
      <span v-for="doc in physicians" :key="doc" class="doc">
        <img 
          v-bind:src="doc.img" 
          v-bind:alt="doc.name"
          class="small_image_display">
      </span>
    </div>
  </main>
</template>
<style scoped>
div.doctorsdisplay {
  margin-top: 24px;
  text-align: center;
}
img.small_image_display {
  height: 96px;
  padding: 5px;
}
</style>