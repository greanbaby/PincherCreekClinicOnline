<script setup>
/** Pincher Creek Clinic Online
 * 
 * This page contains the physicians array with links to physician pictures
 * 
 * @author Scott Gingras March 29, 2023
 */
import { RouterLink, RouterView } from 'vue-router'
import HelloClinic from './components/HelloClinic.vue'
import { ref, computed } from 'vue'

/** physicians
 * physicians is an array of physician objects with name and img
 * where img is the url link to the /public folder to their picture
 */
const physicians = ref([ 
  { name: 'Ashley_Rommens',
    img: '/physicians/A_Rommens.jpg',
    panelsize: 1327
  },
  { name: 'Bev_Burton',
    img: '/physicians/B_Burton.jpg',
    panelsize: 1609
  },
  { name: 'Clinic_Panel',
    img: '/physicians/Clinic_Panel.jpg',
    panelsize: 2472
  },
  { name: 'Gavin_Parker',
    img: '/physicians/G_Parker.jpg',
    panelsize: 1614
  },
  { name: 'Jared_Van_Bussel',
    img: '/physicians/J_Van_Bussel.jpg',
    panelsize: 906
  },
  { name: 'Tracy_Burton',
    img: '/physicians/T_Burton.jpg',
    panelsize: 1612
  },
  { name: 'TOTAL',
    img: '/team.svg',
    panelsize: 9011
  }
]);

const seedAI = 78; // Number of images in the /public/ai folder

// randomNumber determines which image is displayed
let randomNumber = ref((Math.floor(Math.random() * seedAI) + 1));

// COMPUTED randomNumberSource to get string url to randomNumber image
const randomNumberSource = computed(() => {
  return '/ai/' + randomNumber.value + '.jpg';
});

// changePic is called every time somebody clicks the image
function changePic() {
  if (randomNumber.value === seedAI) {
    randomNumber.value = 1;  // no more pictures left so reset back to start
  } else {
    randomNumber.value = randomNumber.value + 1;  // go to next picture
  }
}
</script>

<template>
  <header class="no-print">
    
    <img :src="randomNumberSource" @click="changePic" width="135" height="135" class="logo">

    <div class="wrapper">
      <HelloClinic msg="Pincher Creek Clinic" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/improvement">Improvement</RouterLink>
        <RouterLink to="/physician">Physicians</RouterLink>
        <RouterLink to="/reports">Reports</RouterLink>
        <RouterLink to="/tools">Tools</RouterLink>
      </nav>

    </div>

  </header>

  <RouterView :physicians = physicians />
</template>

<style>
@media print {
  .no-print {
    display: none !important;
  }
}
body {
  color: #222;
  background-color: white;
}
h1,h2,h3,h4 {
  color: hsla(160, 100%, 37%, 1);
}
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: #222;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
/* spacing */

table {
  table-layout: fixed;
  width: 100%;
  border-collapse: collapse;
}

thead th:nth-child(1) {
  width: 40%;
}

thead th:nth-child(2) {
  width: 15%;
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
/* typography */


thead th,
tfoot th {
  font-family: "helvetica neue", helvetica, arial, sans-serif;
}

th {
  font-family: "helvetica neue", helvetica, arial, sans-serif;
  letter-spacing: 0px;
}

td {
  font-family: "helvetica neue", helvetica, arial, sans-serif;
  letter-spacing: 1px;
}

tbody td {
  font-family: "helvetica neue", helvetica, arial, sans-serif;
  text-align: center;
}

tfoot th {
  text-align: right;
}

.strongly {
  font-weight: bold;
}

/* striping */

tbody tr:nth-child(odd) {
  background-color: white;
}

tbody tr:nth-child(even) {
  background-color: rgb(226, 226, 226);
}

table {
  background-color: hsla(160, 100%, 37%, 0.1);
}
caption {
  font-family: "helvetica neue", helvetica, arial, sans-serif;
  font-size: larger;
  padding: 10px;
  font-style: italic;
  caption-side: bottom;
  color: #331;
  text-align: right;
  letter-spacing: 1px;
}

select {
  font-family: "helvetica neue", helvetica, arial, sans-serif;
  padding: 4px;
}
.tab-button {
  font-family: "helvetica neue", helvetica, arial, sans-serif;
  padding: 8px 16px;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  border: 1px solid #ccc;
  cursor: pointer;
  background: #f0f0f0;
  margin-bottom: -1px;
  margin-right: -1px;
}
.tab-button:hover {
  background: #e0e0e0;
}
.tab-button.active {
  background: hsla(160, 100%, 37%, 0.5);
  font-weight: bold;
}
.tab {
  border: 1px solid #ccc;
  padding: 10px;
}
</style>
