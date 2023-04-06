<template>
<div class="rptWrap">
  <div class="flex-column">
    <div class="column-item">
      <img alt="Actions" src="@/assets/bulb-education-idea.svg" width="100" height="100" />
    </div>
    <div class="column-item">
      <h1>Improvement Actions</h1>
    </div>
  </div>

  <h2>To-Do Items From Improvement Meetings</h2>

  <hr>

  
</div>

</template>
<style scoped>
.flex-column {
  margin-top: 10px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 15px;
}
.column-item {
  padding: 0px;
  margin-top:10px;
}
.rptWrap {
  border: 1px solid hsla(160, 100%, 37%, 0.5);
  margin-top: 0px;
  padding: 6px;
}
h2 {
  padding-left: 30px;
}
p {
  padding: 30px;
}
</style>