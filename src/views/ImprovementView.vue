<script setup>
/** ImprovementView.vue
 * 
 * This page contains the TAB looking button interface for Improvements
 * 
 * @author Scott Gingras April 5, 2023
 */
import { ref } from 'vue';
import Actions from '/src/components/Improvement/Actions/improvementActions.vue';
import Minutes from '/src/components/Improvement/Minutes/improvementMinutes.vue';

const currentTab = ref('Minutes');

const tabs = {
  Actions,
  Minutes
}
</script>
<template>
  <div class="improvement">
    <button
      v-for="(_, tab) in tabs"
        :key="tab"
        :class="['tab-button', { active: currentTab === tab }]"
        @click="currentTab = tab"
    >
      {{ tab }}
    </button>

    <component :is="tabs[currentTab]" class="tab"></component>

  </div>
</template>
<style scoped>
@media (min-width: 1024px) {
  .improvement {
    min-height: 100vh;
    align-items: center;
  }
}
</style>
