<template>
  <div class="rptWrap">
    <div class="flex-column">
      <div class="column-item">
        <img alt="Anxious" src="@/assets/anxious-face.svg" width="100" height="100" />

      </div>
      <div class="column-item">
        <p>Improvement Minutes</p>
      </div>
    </div>
  </div>

</template>
<style scoped>
.flex-column {
  margin-top: 10px;
  display: grid;
  grid-template-columns: (1fr, 1fr);
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
</style>