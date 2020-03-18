<template>
  <div class="grid-quotes">
    <slot></slot>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.grid-quotes {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 20px;
}

.quote {
  display: inline-block;
  font-family: 'Arizonia';
  font-size: 25px;
  padding: 10px;
  border: solid lightgrey 1px;
  cursor: pointer;
}

.quote:hover {
  background-color: lightcoral;
}
</style>
