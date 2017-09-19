<template>
  <div class="cell" v-bind:style="styles">{{ row + '.' + col }}</div>
</template>

<script>
export default {
  name: 'cell',
  props: {
    styles: Object,
    row: Number,
    col: Number
  }
};
</script>

<style scoped>
div {
  display: inline-block;
}
</style>
