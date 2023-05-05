<script setup>

</script>
<template>
  <div class="tool">
    <div class="flex-column">
      
      <div class="column-item">
        <h1>Patient Handouts and Community Links</h1>
      </div>

    </div>

  <p>Click this link for Patient Care Handouts from AHS: <a href="https://myhealth.alberta.ca/Health/aftercareinformation/Pages/default.aspx" target="_blank">PATIENT CARE HANDOUTS</a></p>

  <p><object data="https://chinookprimarycarenetwork.ab.ca/userfile/file/Getting Connected Booklet June 2022.pdf" type="application/pdf" width="100%" height="800px"></object></p>
  
  </div>
  
</template>
<style scoped>
.flex-column {
  margin-top: 10px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 15px;
}
/* grid-template-columns: 1fr 1fr; */
.column-item {
  padding: 0px;
  margin-top:10px;
}
.tool {
  border: 1px solid hsla(160, 100%, 37%, 0.5);
  margin-top: 0px;
  padding: 6px;
}
h1 {
  margin-top: 2px;
}
h2 {
  padding-left: 30px;
}
p {
  padding: 30px;
}
</style>
