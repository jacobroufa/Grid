<template>
  <div class="grid">
    <div class="row"
      v-for="row in h">
      <div class="col"
        v-for="col in v">
        <Cell v-bind:row="row" v-bind:col="col" v-bind:styles="style" v-on:click="cellHover" />
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
      offsetHeight: 0,
      cellColor: 'inherit'
    };
  },
  components: {
    Cell
  },
  props: ['h', 'v'],
  ready() {
    const rect = this.$el.getBoundingClientRect();

    this.offsetHeight = rect.top;
  },
  methods: {
    cellHover() {
      this.cellColor = '#f00';
    }
  },
  computed: {
    style() {
      const aspect = window.innerHeight / window.innerWidth;
      const width = window.innerWidth * (2 / 3);
      const height = ((window.innerHeight * (6 / 7)) - this.offsetHeight) * aspect;

      return {
        width: `${Math.ceil(width / this.h)}px`,
        height: `${Math.ceil(height / this.v)}px`,
        backgroundColor: this.cellColor
      };
    }
  }
};
</script>

<style scoped>
.col {
  display: inline-block;
}
</style>
