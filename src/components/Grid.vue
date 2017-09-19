<template>
  <div class="grid">
    <div class="row"
      v-for="row in h">
      <div class="col"
        v-for="col in v">
        <Cell v-bind:row="row" v-bind:col="col" v-bind:styles="style" />
      </div>
    </div>
  </div>
</template>

<script>
import Cell from './Cell';

export default {
  name: 'grid',
  data() {
    return {
      col: null,
      row: null,
      offsetHeight: 0
    };
  },
  components: {
    Cell
  },
  props: {
    h: Number,
    v: Number
  },
  computed: {
    style() {
      const width = window.innerWidth * (2 / 3);
      const aspect = window.innerWidth / window.innerHeight;
      const height = (window.innerHeight - this.offsetHeight) * aspect;

      return {
        width: `${Math.ceil(width / this.h)}px`,
        height: `${Math.ceil(height / this.v)}px`
      };
    }
  },
  ready() {
    this.offsetHeight = this.$el.offsetHeight;
  }
};
</script>

<style scoped>
.col {
  display: inline-block;
}
</style>
