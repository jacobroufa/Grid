<template>
  <div id="app">
    <h1>Grid Demo</h1>

    <hr>

    <label>
      <span v-if="!square">Horizontal: </span>
      <span v-else>Grid Size: </span>
      <input v-model.number="size" type="text">
    </label>

    <label v-if="!square">
      <span>Vertical: </span>
      <input v-model.number="vSize" type="text">
    </label>

    <label>Square Grid? <input v-model.boolean="square" v-on:change="squareGrid" type="checkbox"></label>

    <hr>

    <Grid v-bind:h="size" v-bind:v="vSize" />
  </div>
</template>

<script>
import Grid from './components/Grid';

export default {
  name: 'gridDemo',
  components: {
    Grid
  },
  data() {
    return {
      square: true,
      size: 4,
      vSize: 4
    };
  },
  methods: {
    squareGrid(isSquare) {
      if (isSquare) {
        this.vSize = this.size;
      }
    }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
