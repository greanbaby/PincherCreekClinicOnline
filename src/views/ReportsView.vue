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
import TT3N from '/src/components/Reports/TT3N.vue';
import Visits from '/src/components/Reports/Visits/rptVisits.vue'
defineProps(['repertoires', 'physicians', 'noshows', 'visits']);
const currentTab = ref('Prevention');
const tabs = {
  NoShows,
  Prevention,
  TT3N,
  Visits
  
}
const repertoires = ref([
  // Apr. 10, 2023  (Month is 0-indexed)
  {
    time_period: new Date(2023,3,10),
    touchstones: [
      // Ashley_Rommens
      {
        physician: "Ashley_Rommens",
        BP_Numerator: 405,
        BP_Denominator: 962,
        CRC_Numerator: 164,
        CRC_Denominator: 385,
        Exercise_Numerator: 380,
        Exercise_Denominator: 962,
        Height_Numerator: 925,
        Height_Denominator: 962,
        Mammo_Numerator: 138,
        Mammo_Denominator: 268,
        Pap_Numerator: 213,
        Pap_Denominator: 393,
        Smoking_Numerator: 384,
        Smoking_Denominator: 962,
        Weight_Numerator: 622,
        Weight_Denominator: 962,
      },
      // Bev_Burton
      {
        physician: "Bev_Burton",
        BP_Numerator: 531,
        BP_Denominator: 1149,
        CRC_Numerator: 148,
        CRC_Denominator: 420,
        Exercise_Numerator: 498,
        Exercise_Denominator: 1149,
        Height_Numerator: 1092,
        Height_Denominator: 1149,
        Mammo_Numerator: 168,
        Mammo_Denominator: 296,
        Pap_Numerator: 242,
        Pap_Denominator: 461,
        Smoking_Numerator: 506,
        Smoking_Denominator: 1149,
        Weight_Numerator: 747,
        Weight_Denominator: 1149,
      },
      // Clinic_Panel
      {
        physician: "Clinic_Panel",
        BP_Numerator: 761,
        BP_Denominator: 1946,
        CRC_Numerator: 236,
        CRC_Denominator: 765,
        Exercise_Numerator: 779,
        Exercise_Denominator: 1946,
        Height_Numerator: 1715,
        Height_Denominator: 1946,
        Mammo_Numerator: 120,
        Mammo_Denominator: 318,
        Pap_Numerator: 235,
        Pap_Denominator: 587,
        Smoking_Numerator: 780,
        Smoking_Denominator: 1946,
        Weight_Numerator: 1114,
        Weight_Denominator: 1946,
      },
      // Gavin_Parker
      {
        physician: "Gavin_Parker",
        BP_Numerator: 423,
        BP_Denominator: 1374,
        CRC_Numerator: 180,
        CRC_Denominator: 592,
        Exercise_Numerator: 431,
        Exercise_Denominator: 1374,
        Height_Numerator: 1256,
        Height_Denominator: 1374,
        Mammo_Numerator: 111,
        Mammo_Denominator: 254,
        Pap_Numerator: 160,
        Pap_Denominator: 334,
        Smoking_Numerator: 430,
        Smoking_Denominator: 1374,
        Weight_Numerator: 713,
        Weight_Denominator: 1374,
      },
      // Jared_Van_Bussel
      {
        physician: "Jared_Van_Bussel",
        BP_Numerator: 287,
        BP_Denominator: 722,
        CRC_Numerator: 120,
        CRC_Denominator: 304,
        Exercise_Numerator: 283,
        Exercise_Denominator: 722,
        Height_Numerator: 692,
        Height_Denominator: 722,
        Mammo_Numerator: 63,
        Mammo_Denominator: 119,
        Pap_Numerator: 79,
        Pap_Denominator: 191,
        Smoking_Numerator: 284,
        Smoking_Denominator: 722,
        Weight_Numerator: 441,
        Weight_Denominator: 722,
      },
      // Tracy_Burton
      {
        physician: "Tracy_Burton",
        BP_Numerator: 546,
        BP_Denominator: 1203,
        CRC_Numerator: 184,
        CRC_Denominator: 458,
        Exercise_Numerator: 515,
        Exercise_Denominator: 1203,
        Height_Numerator: 1130,
        Height_Denominator: 1203,
        Mammo_Numerator: 160,
        Mammo_Denominator: 320,
        Pap_Numerator: 253,
        Pap_Denominator: 456,
        Smoking_Numerator: 518,
        Smoking_Denominator: 1203,
        Weight_Numerator: 803,
        Weight_Denominator: 1203,
      },
      // TOTAL
      {
        physician: "TOTAL",
        BP_Numerator: 2953,
        BP_Denominator: 7364,
        CRC_Numerator: 1032,
        CRC_Denominator: 2926,
        Exercise_Numerator: 2886,
        Exercise_Denominator: 7364,
        Height_Numerator: 6811,
        Height_Denominator: 7364,
        Mammo_Numerator: 760,
        Mammo_Denominator: 1578,
        Pap_Numerator: 1182,
        Pap_Denominator: 2424,
        Smoking_Numerator: 2902,
        Smoking_Denominator: 7364,
        Weight_Numerator: 4440,
        Weight_Denominator: 7364,
      }
    ]
  },
  // Mar. 7, 2023  
  {
    time_period: new Date(2023,2,7),
    touchstones: [
      // Ashley_Rommens
      {
        physician: "Ashley_Rommens",
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
      // Bev_Burton
      {
        physician: "Bev_Burton",
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
      // Gavin_Parker
      {
        physician: "Gavin_Parker",
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
      // Jared_Van_Bussel
      {
        physician: "Jared_Van_Bussel",
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
      // Tracy_Burton
      {
        physician: "Tracy_Burton",
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
      // Ashley_Rommens
      {
        physician: "Ashley_Rommens",
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
      // Bev_Burton
      {
        physician: "Bev_Burton",
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
      // Gavin_Parker
      {
        physician: "Gavin_Parker",
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
      // Jared_Van_Bussel
      {
        physician: "Jared_Van_Bussel",
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
      // Tracy_Burton
      {
        physician: "Tracy_Burton",
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
      // Ashley_Rommens
      {
        physician: "Ashley_Rommens",
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
      // Bev_Burton
      {
        physician: "Bev_Burton",
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
      // Gavin_Parker
      {
        physician: "Gavin_Parker",
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
      // Jared_Van_Bussel
      {
        physician: "Jared_Van_Bussel",
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
      // Tracy_Burton
      {
        physician: "Tracy_Burton",
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
const noshows = ref([
  // Apr. 20, 2023  (Month is 0-indexed)
  {
    time_period: new Date(2023,3,20),
    touchstones: [
      // Appointments_Nursing
      {
        provider: "Appointments_Nursing",
        noshows_1month: 16,
        noshows_3month: 43,
        noshows_6month: 77,
        noshows_12month: 121,
      },
      // Burton_Bev
      {
        provider: "Burton_Bev",
        noshows_1month: 16,
        noshows_3month: 45,
        noshows_6month: 100,
        noshows_12month: 175,
      },
      // Burton_Tracy
      {
        provider: "Burton_Tracy",
        noshows_1month: 12,
        noshows_3month: 29,
        noshows_6month: 59,
        noshows_12month: 113,
      },
      // Craig_Tess
      {
        provider: "Craig_Tess",
        noshows_1month: 2,
        noshows_3month: 3,
        noshows_6month: 6,
        noshows_12month: 7,
      },
      // Dolan_Cheryl
      {
        provider: "Dolan_Cheryl",
        noshows_1month: 9,
        noshows_3month: 28,
        noshows_6month: 61,
        noshows_12month: 143,
      },
      // Gelber_Tobias
      {
        provider: "Gelber_Tobias",
        noshows_1month: 0,
        noshows_3month: 0,
        noshows_6month: 0,
        noshows_12month: 36,
      },
      // Gerber_Susan
      {
        provider: "Gerber_Susan",
        noshows_1month: 1,
        noshows_3month: 4,
        noshows_6month: 6,
        noshows_12month: 13,
      },
      // Hackett_Finola
      {
        provider: "Hackett_Finola",
        noshows_1month: 0,
        noshows_3month: 1,
        noshows_6month: 1,
        noshows_12month: 1,
      },
      // Kiss_Douglas
      {
        provider: "Kiss_Douglas",
        noshows_1month: 0,
        noshows_3month: 0,
        noshows_6month: 2,
        noshows_12month: 15,
      },
      // Lach_Christopher
      {
        provider: "Lach_Christopher",
        noshows_1month: 0,
        noshows_3month: 0,
        noshows_6month: 62,
        noshows_12month: 97,
      },
      // Lewis_Larissa
      {
        provider: "Lewis_Larissa",
        noshows_1month: 1,
        noshows_3month: 5,
        noshows_6month: 5,
        noshows_12month: 7,
      },
      // Mitchell_Cathy
      {
        provider: "Mitchell_Cathy",
        noshows_1month: 2,
        noshows_3month: 7,
        noshows_6month: 13,
        noshows_12month: 19,
      },
      // Parker_Gavin
      {
        provider: "Parker_Gavin",
        noshows_1month: 24,
        noshows_3month: 55,
        noshows_6month: 105,
        noshows_12month: 299,
      },
      // Quick_Jacqueline
      {
        provider: "Quick_Jacqueline",
        noshows_1month: 1,
        noshows_3month: 6,
        noshows_6month: 13,
        noshows_12month: 28,
      },
      // Rommens_Ashley
      {
        provider: "Rommens_Ashley",
        noshows_1month: 20,
        noshows_3month: 35,
        noshows_6month: 63,
        noshows_12month: 156,
      },
      // Shamsi_Shahrab_Parisa
      {
        provider: "Shamsi_Shahrab_Parisa",
        noshows_1month: 0,
        noshows_3month: 0,
        noshows_6month: 0,
        noshows_12month: 1,
      },
      // Stephens_Mark
      {
        provider: "Stephens_Mark",
        noshows_1month: 0,
        noshows_3month: 7,
        noshows_6month: 9,
        noshows_12month: 9,
      },
      // Van_Bussel_Jared
      {
        provider: "Van_Bussel_Jared",
        noshows_1month: 9,
        noshows_3month: 13,
        noshows_6month: 38,
        noshows_12month: 91,
      },
      // Z_TOTAL
      {
        provider: "Z_TOTAL",
        noshows_1month: 113,
        noshows_3month: 281,
        noshows_6month: 620,
        noshows_12month: 1331,
      }
    ]
  }
]);
const visits = ref([
  // Apr. 25, 2023  (Month is 0-indexed)
  {
    time_period: new Date(2023,3,25),
    touchstones: [
      // Appointments_Nursing
      {
        provider: "Appointments_Nursing",
        visits_1month: 207,
        visits_3month: 483,
        visits_6month: 806,
        visits_12month: 1365,
      },
      {
        provider: "Bailey_Robert",
        visits_1month: 0,
        visits_3month: 18,
        visits_6month: 18,
        visits_12month: 18,
      },
      {
        provider: "Biernacki_Mark",
        visits_1month: 0,
        visits_3month: 0,
        visits_6month: 6,
        visits_12month: 6,
      },
      {
        provider: "Burton_Bev",
        visits_1month: 304,
        visits_3month: 1103,
        visits_6month: 2288,
        visits_12month: 4478,
      },
      {
        provider: "Burton_Tracy",
        visits_1month: 386,
        visits_3month: 1210,
        visits_6month: 2449,
        visits_12month: 4627,
      },
      {
        provider: "Craig_Tess",
        visits_1month: 10,
        visits_3month: 21,
        visits_6month: 43,
        visits_12month: 51,
      },
      {
        provider: "Dolan_Cheryl",
        visits_1month: 87,
        visits_3month: 206,
        visits_6month: 413,
        visits_12month: 870,
      },
      {
        provider: "Gelber_Tobias",
        visits_1month: 0,
        visits_3month: 0,
        visits_6month: 1,
        visits_12month: 694,
      },
      {
        provider: "Gerber_Susan",
        visits_1month: 78,
        visits_3month: 246,
        visits_6month: 443,
        visits_12month: 899,
      },
      {
        provider: "Hackett_Finola",
        visits_1month: 0,
        visits_3month: 14,
        visits_6month: 14,
        visits_12month: 14,
      },
      {
        provider: "Kiss_Douglas",
        visits_1month: 0,
        visits_3month: 0,
        visits_6month: 46,
        visits_12month: 277,
      },
      {
        provider: "Lach_Christopher",
        visits_1month: 0,
        visits_3month: 0,
        visits_6month: 782,
        visits_12month: 1437,
      },
      {
        provider: "Lewis_Larissa",
        visits_1month: 11,
        visits_3month: 23,
        visits_6month: 49,
        visits_12month: 85,
      },
      {
        provider: "Mitchell_Cathy",
        visits_1month: 24,
        visits_3month: 94,
        visits_6month: 190,
        visits_12month: 379,
      },
      {
        provider: "Parker_Gavin",
        visits_1month: 221,
        visits_3month: 725,
        visits_6month: 1483,
        visits_12month: 3365,
      },
      {
        provider: "Quick_Jacqueline",
        visits_1month: 11,
        visits_3month: 42,
        visits_6month: 64,
        visits_12month: 118,
      },
      {
        provider: "Reeves_Janine",
        visits_1month: 0,
        visits_3month: 0,
        visits_6month: 0,
        visits_12month: 480,
      },
      {
        provider: "Rommens_Ashley",
        visits_1month: 193,
        visits_3month: 518,
        visits_6month: 1131,
        visits_12month: 2394,
      },
      {
        provider: "Shamsi_Shahrab_Parisa",
        visits_1month: 0,
        visits_3month: 0,
        visits_6month: 0,
        visits_12month: 17,
      },
      {
        provider: "Stephens_Mark",
        visits_1month: 6,
        visits_3month: 144,
        visits_6month: 256,
        visits_12month: 256,
      },
      {
        provider: "Van_Bussel_Jared",
        visits_1month: 174,
        visits_3month: 531,
        visits_6month: 1259,
        visits_12month: 2642,
      },
      {
        provider: "Z_TOTAL",
        visits_1month: 1712,
        visits_3month: 5379,
        visits_6month: 11742,
        visits_12month: 24472,
      },
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

    <component :is="tabs[currentTab]" class="tab" :repertoires=repertoires :noshows=noshows :physicians=physicians :visits=visits></component>
    
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .reports {
    min-height: 100vh;
    align-items: center;
  }
}
.flex-column {
  margin-top: 1px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  /* grid-template-columns: repeat(3, 1fr); */
  grid-gap: 15px;
}

.column-item {
  padding: 0px;
  margin-top:1px;
}
.rptWrap {
  border: 1px solid hsla(160, 100%, 37%, 0.5);
  border-bottom: 0px;
  margin-top: 0px;
  padding: 6px;
}
</style>