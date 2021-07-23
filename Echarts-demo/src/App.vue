<template>
  <div id="app">
    <barCharts :xDate="xDate" />
  </div>
</template>

<script>
import barCharts from "./components/barCharts.vue";
export default {
  name: "App",
  components: {
    barCharts
  },
  data() {
    return {
      xDate: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
