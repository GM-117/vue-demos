<template>
  <div id="app">
    <Header/>
    <List/>
  </div>
</template>

<script>
import Header from './components/header.vue'
import List from './components/list.vue'

export default {
  name: 'App',
  components: {
    Header,
    List
  }
}
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
