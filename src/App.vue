<template>
  <div id="app">
    <TreeBrowser />
  </div>
</template>

<script>
import TreeBrowser from './components/TreeBrowser.vue';

export default {
  name: 'App',
  components: {
    TreeBrowser,
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
  margin-top: 0px;
  height: 100vh;
}
</style>
