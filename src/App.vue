<template>
  <div id="app">
    <Sidebar />
    <TreeBrowser v-bind:resource_url="'https://raw.githubusercontent.com/KenepaTech/kenepa-tree/main/data/kenepa_resources_nested.json'" />
  </div>
</template>

<script>
import Vue from 'vue';
import Buefy from 'buefy';
import 'buefy/dist/buefy.css';

import TreeBrowser from './components/TreeBrowser.vue';
import Sidebar from './components/Sidebar.vue';

Vue.use(Buefy)

export default {
  name: 'App',
  components: {
    TreeBrowser,
    Sidebar,
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
