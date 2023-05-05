<script setup>
/** ToolsView.vue
 * 
 * This page contains the TAB looking button interface for choosing a Tool
 * 
 * @author Scott Gingras March 30, 2023
 */
import { ref } from 'vue';
import Handouts from '/src/components/Tools/Handouts.vue';
import AddPanelNames from '/src/components/Tools/AddPanelNames/toolAddPanelNames.vue';
import PanelCount from '/src/components/Tools/PanelCount/toolPanelCount.vue';
import RemoveRowsNotMatching from '/src/components/Tools/RemoveRowsNotMatching/toolRemoveRowsNotMatching.vue';

const currentTab = ref('Handouts');

const tabs = {
  Handouts,
  AddPanelNames,
  PanelCount,
  RemoveRowsNotMatching
}
</script>
<template>
  <div class="tools">
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
  .tools {
    min-height: 100vh;
    align-items: center;
  }
}
</style>
