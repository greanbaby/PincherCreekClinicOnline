<template>
  <div class="tool">
    <div class="flex-column">
      <div class="column-item">
        imgRemoveRows
      </div>
      <div class="column-item">
        <p>Tool Remove Rows Not Matching:<br>


        </p>
      </div>
      <div class="column-item">
       
      </div>
    </div>
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
</style>