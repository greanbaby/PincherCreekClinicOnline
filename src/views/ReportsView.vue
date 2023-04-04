<script setup>
/** ReportsView.vue
 * 
 * This page contains the TAB looking button interface for choosing a Report
 * 
 * @author Scott Gingras March 30, 2023
 */
import { ref } from 'vue';
import Prevention from '/src/components/Reports/Prevention/rptPrevention.vue';
import NoShows from '/src/components/Reports/NoShows/rptNoShows.vue';
defineProps(['repertoires', 'physicians']);

const currentTab = ref('Prevention');

const tabs = {
  NoShows,
  Prevention
  
}

const repertoires = ref([
    // Mar. 7, 2023  
    {
    time_period: new Date(2023,2,7),
    touchstones: [
      // A_Rommens
      {
        physician: "A_Rommens",
        BP_Numerator: 0,
        BP_Denominator: 969,
        CRC_Numerator: 169,
        CRC_Denominator: 388,
        Exercise_Numerator: 399,
        Exercise_Denominator: 969,
        Height_Numerator: 931,
        Height_Denominator: 969,
        Mammo_Numerator: 142,
        Mammo_Denominator: 270,
        Pap_Numerator: 214,
        Pap_Denominator: 401,
        Smoking_Numerator: 404,
        Smoking_Denominator: 969,
        Weight_Numerator: 613,
        Weight_Denominator: 969,
      },
      // B_Burton
      {
        physician: "B_Burton",
        BP_Numerator: 0,
        BP_Denominator: 1156,
        CRC_Numerator: 153,
        CRC_Denominator: 421,
        Exercise_Numerator: 530,
        Exercise_Denominator: 1156,
        Height_Numerator: 1093,
        Height_Denominator: 1156,
        Mammo_Numerator: 158,
        Mammo_Denominator: 296,
        Pap_Numerator: 252,
        Pap_Denominator: 491,
        Smoking_Numerator: 538,
        Smoking_Denominator: 1156,
        Weight_Numerator: 736,
        Weight_Denominator: 1156,
      },
      // Clinic_Panel
      {
        physician: "Clinic_Panel",
        BP_Numerator: 0,
        BP_Denominator: 1941,
        CRC_Numerator: 240,
        CRC_Denominator: 769,
        Exercise_Numerator: 793,
        Exercise_Denominator: 1941,
        Height_Numerator: 1714,
        Height_Denominator: 1941,
        Mammo_Numerator: 117,
        Mammo_Denominator: 317,
        Pap_Numerator: 242,
        Pap_Denominator: 614,
        Smoking_Numerator: 793,
        Smoking_Denominator: 1941,
        Weight_Numerator: 1094,
        Weight_Denominator: 1941,
      },
      // G_Parker
      {
        physician: "G_Parker",
        BP_Numerator: 0,
        BP_Denominator: 1387,
        CRC_Numerator: 187,
        CRC_Denominator: 594,
        Exercise_Numerator: 440,
        Exercise_Denominator: 1387,
        Height_Numerator: 1265,
        Height_Denominator: 1387,
        Mammo_Numerator: 109,
        Mammo_Denominator: 255,
        Pap_Numerator: 175,
        Pap_Denominator: 354,
        Smoking_Numerator: 437,
        Smoking_Denominator: 1387,
        Weight_Numerator: 702,
        Weight_Denominator: 1387,
      },
      // J_Van_Bussel
      {
        physician: "J_Van_Bussel",
        BP_Numerator: 0,
        BP_Denominator: 719,
        CRC_Numerator: 115,
        CRC_Denominator: 303,
        Exercise_Numerator: 284,
        Exercise_Denominator: 719,
        Height_Numerator: 688,
        Height_Denominator: 719,
        Mammo_Numerator: 63,
        Mammo_Denominator: 120,
        Pap_Numerator: 85,
        Pap_Denominator: 201,
        Smoking_Numerator: 285,
        Smoking_Denominator: 719,
        Weight_Numerator: 434,
        Weight_Denominator: 719,
      },
      // T_Burton
      {
        physician: "T_Burton",
        BP_Numerator: 0,
        BP_Denominator: 1206,
        CRC_Numerator: 183,
        CRC_Denominator: 455,
        Exercise_Numerator: 534,
        Exercise_Denominator: 1206,
        Height_Numerator: 1130,
        Height_Denominator: 1206,
        Mammo_Numerator: 155,
        Mammo_Denominator: 319,
        Pap_Numerator: 255,
        Pap_Denominator: 470,
        Smoking_Numerator: 536,
        Smoking_Denominator: 1206,
        Weight_Numerator: 792,
        Weight_Denominator: 1206,
      },
      // TOTAL
      {
        physician: "TOTAL",
        BP_Numerator: 0,
        BP_Denominator: 7388,
        CRC_Numerator: 1047,
        CRC_Denominator: 2933,
        Exercise_Numerator: 2981,
        Exercise_Denominator: 7388,
        Height_Numerator: 6823,
        Height_Denominator: 7388,
        Mammo_Numerator: 744,
        Mammo_Denominator: 1578,
        Pap_Numerator: 1223,
        Pap_Denominator: 2533,
        Smoking_Numerator: 2994,
        Smoking_Denominator: 7388,
        Weight_Numerator: 4372,
        Weight_Denominator: 7388,
      }
    ]
  },
    // Jan. 31, 2023  
    {
    time_period: new Date(2023,0,31),
    touchstones: [
      // A_Rommens
      {
        physician: "A_Rommens",
        BP_Numerator: 399,
        BP_Denominator: 989,
        CRC_Numerator: 171,
        CRC_Denominator: 395,
        Exercise_Numerator: 377,
        Exercise_Denominator: 989,
        Height_Numerator: 901,
        Height_Denominator: 989,
        Mammo_Numerator: 138,
        Mammo_Denominator: 273,
        Pap_Numerator: 212,
        Pap_Denominator: 408,
        Smoking_Numerator: 382,
        Smoking_Denominator: 989,
        Weight_Numerator: 629,
        Weight_Denominator: 989,
      },
      // B_Burton
      {
        physician: "B_Burton",
        BP_Numerator: 533,
        BP_Denominator: 1161,
        CRC_Numerator: 155,
        CRC_Denominator: 418,
        Exercise_Numerator: 511,
        Exercise_Denominator: 1161,
        Height_Numerator: 1046,
        Height_Denominator: 1161,
        Mammo_Numerator: 159,
        Mammo_Denominator: 296,
        Pap_Numerator: 234,
        Pap_Denominator: 498,
        Smoking_Numerator: 518,
        Smoking_Denominator: 1161,
        Weight_Numerator: 743,
        Weight_Denominator: 1161,
      },
      // Clinic_Panel
      {
        physician: "Clinic_Panel",
        BP_Numerator: 730,
        BP_Denominator: 1990,
        CRC_Numerator: 248,
        CRC_Denominator: 792,
        Exercise_Numerator: 764,
        Exercise_Denominator: 1990,
        Height_Numerator: 1593,
        Height_Denominator: 1990,
        Mammo_Numerator: 119,
        Mammo_Denominator: 328,
        Pap_Numerator: 220,
        Pap_Denominator: 629,
        Smoking_Numerator: 767,
        Smoking_Denominator: 1990,
        Weight_Numerator: 1119,
        Weight_Denominator: 1990,
      },
      // G_Parker
      {
        physician: "G_Parker",
        BP_Numerator: 390,
        BP_Denominator: 1407,
        CRC_Numerator: 189,
        CRC_Denominator: 608,
        Exercise_Numerator: 422,
        Exercise_Denominator: 1407,
        Height_Numerator: 1193,
        Height_Denominator: 1407,
        Mammo_Numerator: 112,
        Mammo_Denominator: 260,
        Pap_Numerator: 151,
        Pap_Denominator: 367,
        Smoking_Numerator: 418,
        Smoking_Denominator: 1407,
        Weight_Numerator: 735,
        Weight_Denominator: 1407,
      },
      // J_Van_Bussel
      {
        physician: "J_Van_Bussel",
        BP_Numerator: 266,
        BP_Denominator: 726,
        CRC_Numerator: 115,
        CRC_Denominator: 302,
        Exercise_Numerator: 267,
        Exercise_Denominator: 726,
        Height_Numerator: 636,
        Height_Denominator: 726,
        Mammo_Numerator: 62,
        Mammo_Denominator: 119,
        Pap_Numerator: 77,
        Pap_Denominator: 207,
        Smoking_Numerator: 269,
        Smoking_Denominator: 726,
        Weight_Numerator: 437,
        Weight_Denominator: 726,
      },
      // T_Burton
      {
        physician: "T_Burton",
        BP_Numerator: 542,
        BP_Denominator: 1228,
        CRC_Numerator: 190,
        CRC_Denominator: 460,
        Exercise_Numerator: 515,
        Exercise_Denominator: 1228,
        Height_Numerator: 1100,
        Height_Denominator: 1228,
        Mammo_Numerator: 149,
        Mammo_Denominator: 320,
        Pap_Numerator: 234,
        Pap_Denominator: 484,
        Smoking_Numerator: 517,
        Smoking_Denominator: 1228,
        Weight_Numerator: 798,
        Weight_Denominator: 1228,
      },
      // TOTAL
      {
        physician: "TOTAL",
        BP_Numerator: 2861,
        BP_Denominator: 7512,
        CRC_Numerator: 1068,
        CRC_Denominator: 2977,
        Exercise_Numerator: 2857,
        Exercise_Denominator: 7512,
        Height_Numerator: 6677,
        Height_Denominator: 7512,
        Mammo_Numerator: 739,
        Mammo_Denominator: 1597,
        Pap_Numerator: 1119,
        Pap_Denominator: 2595,
        Smoking_Numerator: 2872,
        Smoking_Denominator: 7512,
        Weight_Numerator: 4462,
        Weight_Denominator: 7512,
      }
    ]
  },
  // Dec. 29, 2022
  {
    time_period: new Date(2022,11,29),
    touchstones: [
      // A_Rommens
      {
        physician: "A_Rommens",
        BP_Numerator: 378,
        BP_Denominator: 997,
        CRC_Numerator: 171,
        CRC_Denominator: 397,
        Exercise_Numerator: 373,
        Exercise_Denominator: 997,
        Height_Numerator: 904,
        Height_Denominator: 997,
        Mammo_Numerator: 142,
        Mammo_Denominator: 273,
        Pap_Numerator: 214,
        Pap_Denominator: 411,
        Smoking_Numerator: 378,
        Smoking_Denominator: 997,
        Weight_Numerator: 649,
        Weight_Denominator: 997,
      },
      // B_Burton
      {
        physician: "B_Burton",
        BP_Numerator: 506,
        BP_Denominator: 1167,
        CRC_Numerator: 147,
        CRC_Denominator: 420,
        Exercise_Numerator: 487,
        Exercise_Denominator: 1167,
        Height_Numerator: 1045,
        Height_Denominator: 1167,
        Mammo_Numerator: 154,
        Mammo_Denominator: 296,
        Pap_Numerator: 223,
        Pap_Denominator: 509,
        Smoking_Numerator: 495,
        Smoking_Denominator: 1167,
        Weight_Numerator: 753,
        Weight_Denominator: 1167,
      },
      // Clinic_Panel
      {
        physician: "Clinic_Panel",
        BP_Numerator: 671,
        BP_Denominator: 1976,
        CRC_Numerator: 252,
        CRC_Denominator: 789,
        Exercise_Numerator: 702,
        Exercise_Denominator: 1976,
        Height_Numerator: 1603,
        Height_Denominator: 1976,
        Mammo_Numerator: 120,
        Mammo_Denominator: 331,
        Pap_Numerator: 221,
        Pap_Denominator: 628,
        Smoking_Numerator: 706,
        Smoking_Denominator: 1976,
        Weight_Numerator: 1120,
        Weight_Denominator: 1976,
      },
      // G_Parker
      {
        physician: "G_Parker",
        BP_Numerator: 365,
        BP_Denominator: 1442,
        CRC_Numerator: 190,
        CRC_Denominator: 618,
        Exercise_Numerator: 400,
        Exercise_Denominator: 1442,
        Height_Numerator: 1228,
        Height_Denominator: 1442,
        Mammo_Numerator: 113,
        Mammo_Denominator: 266,
        Pap_Numerator: 154,
        Pap_Denominator: 395,
        Smoking_Numerator: 394,
        Smoking_Denominator: 1442,
        Weight_Numerator: 777,
        Weight_Denominator: 1442,
      },
      // J_Van_Bussel
      {
        physician: "J_Van_Bussel",
        BP_Numerator: 256,
        BP_Denominator: 756,
        CRC_Numerator: 118,
        CRC_Denominator: 313,
        Exercise_Numerator: 256,
        Exercise_Denominator: 756,
        Height_Numerator: 663,
        Height_Denominator: 756,
        Mammo_Numerator: 65,
        Mammo_Denominator: 123,
        Pap_Numerator: 79,
        Pap_Denominator: 218,
        Smoking_Numerator: 257,
        Smoking_Denominator: 756,
        Weight_Numerator: 436,
        Weight_Denominator: 756,
      },
      // T_Burton
      {
        physician: "T_Burton",
        BP_Numerator: 522,
        BP_Denominator: 1238,
        CRC_Numerator: 201,
        CRC_Denominator: 465,
        Exercise_Numerator: 513,
        Exercise_Denominator: 1238,
        Height_Numerator: 1106,
        Height_Denominator: 1238,
        Mammo_Numerator: 143,
        Mammo_Denominator: 325,
        Pap_Numerator: 239,
        Pap_Denominator: 492,
        Smoking_Numerator: 512,
        Smoking_Denominator: 1238,
        Weight_Numerator: 816,
        Weight_Denominator: 1238,
      },
      // TOTAL
      {
        physician: "TOTAL",
        BP_Numerator: 2698,
        BP_Denominator: 7584,
        CRC_Numerator: 1080,
        CRC_Denominator: 3004,
        Exercise_Numerator: 2731,
        Exercise_Denominator: 7584,
        Height_Numerator: 6550,
        Height_Denominator: 7584,
        Mammo_Numerator: 738,
        Mammo_Denominator: 1615,
        Pap_Numerator: 1131,
        Pap_Denominator: 2655,
        Smoking_Numerator: 2742,
        Smoking_Denominator: 7584,
        Weight_Numerator: 4551,
        Weight_Denominator: 7584,
      }
    ]
  }

  
]);

</script>
<template>
  <div class="reports">
    <button
      v-for="(_, tab) in tabs"
        :key="tab"
        :class="['tab-button', { active: currentTab === tab }]"
        @click="currentTab = tab"
    >
      {{ tab }}
    </button>

    <component :is="tabs[currentTab]" class="tab" :repertoires=repertoires :physicians=physicians></component>
    
  </div>
</template>

<style scoped>
@media (min-width: 1024px) {
  .reports {
    min-height: 100vh;
    align-items: center;
  }
}
</style>
