<script setup>
import { ref } from 'vue';
const tt3n = ref([
  {
    datevalue: new Date(2023,4,8),
    average: 85.8,
    
    bb: 72,
    gp: 99,
    jv: 99,
    tb: 73
    
  },
  {
    datevalue: new Date(2023,3,24),
    average: 80,
    
    bb: 72,
    gp: 85,
    jv: 91,
    tb: 72
    
  },
  {
    datevalue: new Date(2023,2,13),
    average: 73,
    ar: 99,
    bb: 62,
    gp: 99,
    jv: 50,
    tb: 55
    
  },
  {
    datevalue: new Date(2023,1,13),
    average: 71.6,
    ar: 66,
    bb: 65,
    gp: 71,
    jv: 99,
    tb: 57
    
  },
  {
    datevalue: new Date(2023,0,30),
    average: 76,
    ar: 65,
    bb: 65,
    gp: 99,
    jv: 88,
    tb: 63
    
  },
  {
    datevalue: new Date(2023,0,16),
    average: 76.8,
    ar: 65,
    bb: 64,
    gp: 99,
    jv: 99,
    tb: 57
    
  },
  {
    datevalue: new Date(2023,0,2),
    average: 53.8,
    ar: 42,
    bb: 52,
    gp: 63,
    jv: 60,
    tb: 52
    
  },
  {
    datevalue: new Date(2022,11,26),
    average: 69.4,
    ar: 49,
    bb: 51,
    gp: 99,
    jv: 99,
    tb: 49
    
  },
  {
    datevalue: new Date(2022,11,12),
    average: 50,
    ar: 53,
    bb: 45,
    gp: 50,
    jv: 53,
    tb: 49
    
  },
  {
    datevalue: new Date(2022,11,5),
    average: 42.8,
    ar: 58,
    bb: 44,
    gp: 59,
    jv: 1,
    tb: 52
    
  },
  {
    datevalue: new Date(2022,10,28),
    average: 72.4,
    ar: 99,
    bb: 59,
    gp: 99,
    jv: 46,
    tb: 59
    
  },
  {
    datevalue: new Date(2022,10,21),
    average: 56.8,
    ar: 21,
    bb: 64,
    gp: 99,
    jv: 50,
    tb: 50
    
  },
  {
    datevalue: new Date(2022,10,14),
    average: 52.4,
    ar: 11,
    bb: 67,
    gp: 73,
    jv: 60,
    tb: 51
    
  },
  {
    datevalue: new Date(2022,9,24),
    average: 73.4,
    ar: 52,
    bb: 99,
    gp: 99,
    jv: 65,
    tb: 52
    
  },
  {
    datevalue: new Date(2022,9,17),
    average: 74.2,
    ar: 59,
    bb: 99,
    gp: 99,
    jv: 58,
    tb: 56
    
  },
  {
    datevalue: new Date(2022,9,10),
    average: 64.4,
    ar: 66,
    bb: 71,
    gp: 70,
    jv: 58,
    tb: 57
    
  },
  {
    datevalue: new Date(2022,9,3),
    average: 62,
    ar: 63,
    bb: 70,
    gp: 70,
    jv: 49,
    tb: 58
    
  },
  {
    datevalue: new Date(2022,8,26),
    average: 64.8,
    ar: 44,
    bb: 65,
    gp: 99,
    jv: 51,
    tb: 65
    
  },
  {
    datevalue: new Date(2022,8,12),
    average: 90.2,
    ar: 99,
    bb: 55,
    gp: 99,
    jv: 99,
    tb: 99
    
  },
  {
    datevalue: new Date(2022,8,5),
    average: 66.6,
    ar: 38,
    bb: 73,
    gp: 99,
    jv: 99,
    tb: 24
    
  },
  {
    datevalue: new Date(2022,7,15),
    average: 91,
    ar: 99,
    bb: 93,
    gp: 99,
    jv: 77,
    tb: 87
    
  },
  {
    datevalue: new Date(2022,7,8),
    average: 85.8,
    ar: 99,
    bb: 70,
    gp: 99,
    jv: 80,
    tb: 81
    
  },
  {
    datevalue: new Date(2022,7,1),
    average: 88.8,
    ar: 93,
    bb: 87,
    gp: 93,
    jv: 86,
    tb: 85
    
  },
  {
    datevalue: new Date(2022,6,18),
    average: 93.8,
    ar: 99,
    bb: 91,
    gp: 99,
    jv: 90,
    tb: 90
    
  },
  {
    datevalue: new Date(2022,5,27),
    average: 97.8,
    ar: 99,
    bb: 99,
    gp: 99,
    jv: 93,
    tb: 99
    
  },
  {
    datevalue: new Date(2022,4,31),
    average: 89,
    ar: 98,
    bb: 78,
    gp: 93,
    jv: 99,
    tb: 77
    
  },




]);
</script>
<template>
  <div class="rptWrap">
    <div class="flex-column">
      <div class="column-item">
        <h2>Time to Third Next Appointment (TT3N)</h2>
      </div>
    </div>


    <h3>Physician 6-Month Averages Apr 20 2023</h3>
    
    <table>
      
      <thead>
        <tr>
          <th>Physician</th>
          <th>Avg. Delay</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Ashley Rommens</td>
          <td>56.8 days</td>
        </tr>

        <tr>
          <td>Bev Burton</td>
          <td>64.3 days</td>
        </tr>

        <tr>
          <td>Gavin Parker</td>
          <td>85.2 days</td>
        </tr>

        <tr>
          <td>Jared Van Bussel</td>
          <td>63.7 days</td>
        </tr>

        <tr>
          <td>Tracy Burton</td>
          <td>54.0 days</td>
        </tr>
        
      </tbody>
    </table>

    <hr>

    <br>
    <h3>Time to Third Next Appointment Delay (in Days)</h3>
    <table>
      
      <thead>
        <tr>
          <th>Date</th>
          <th>Avg.</th>
          <th>AR</th>
          <th>BB</th>
          <th>GP</th>
          <th>JV</th>
          <th>TB</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="touchstone in tt3n" :key="tt3n.datevalue">
          <td>{{ touchstone.datevalue.toLocaleDateString('en-US', { year: 'numeric', month: 'short', day: 'numeric'}) }}</td>
          <td>{{ touchstone.average }}</td>
          <td>{{ touchstone.ar }}</td>
          <td>{{ touchstone.bb }}</td>
          <td>{{ touchstone.gp }}</td>
          <td>{{ touchstone.jv }}</td>
          <td>{{ touchstone.tb }}</td>
        </tr>
      </tbody>
    </table>

  </div>

</template>
<style scoped>
/* spacing */

table {
  table-layout: fixed;
  width: 100%;
  border-collapse: collapse;
}

thead th:nth-child(1) {
  width: 20%;
}

thead th:nth-child(2) {
  width: 10%;
}

thead th:nth-child(3) {
  width: 15%;
}

thead th:nth-child(4) {
  width: 15%;
}

thead th:nth-child(5) {
  width: 15%;
}



th,
td {
  padding: 10px;
}
</style>
