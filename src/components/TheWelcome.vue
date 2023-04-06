<script setup>
/** TheWelcome.vue
 * 
 * This is the HOME PAGE displayed when site first loaded
 * 
 * @author Scott Gingras March 30, 2023
 */
import { RouterLink } from 'vue-router'
import WelcomeItem from './WelcomeItem.vue'

</script>

<template>
  <RouterLink to="/improvement">
    <WelcomeItem>
      <template #icon>
        <img alt="Improvement" src="@/assets/hospital-files.svg" width="44" height="44" />
      </template>
      <template #heading>Improvement</template>
      Action items and minutes from improvement meetings, guides
    </WelcomeItem>
  </RouterLink>

  <RouterLink to="/physician">
    <WelcomeItem>
      <template #icon>
        <img alt="Physician" src="@/assets/doctor.svg" width="68" height="68" />
      </template>
      <template #heading>Physician</template>

      Physician individual focus and summaries
    </WelcomeItem>
  </RouterLink>
  
  <RouterLink to="/reports">
    <WelcomeItem>
      <template #icon>
        <img alt="Reports" src="@/assets/statistics.svg" width="77" height="77" />
      </template>
      <template #heading>Reports</template>
      Panel Details, Prevention and Screening, No Shows
    </WelcomeItem>
  </RouterLink>

  <RouterLink to="/tools">
    <WelcomeItem>
      <template #icon>
        <img alt="Tools" src="@/assets/book-key.svg" width="55" height="55" />
      </template>
      <template #heading>Tools</template>
      Tools for processing and analyzing spreadsheets
    </WelcomeItem>
  </RouterLink>


</template>
