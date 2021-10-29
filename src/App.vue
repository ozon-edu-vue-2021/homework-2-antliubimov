<template>
  <div id="app">
    <tree-address></tree-address>
    <tree :treeData="dataTree"></tree>
  </div>
</template>

<script>
import dataTree from './../public/static/node_modules.json';
import Tree from './components/Tree/Tree';
import TreeAddress from "./components/TreeAddress/TreeAddress";

export default {
  name: 'App',
  data: () => ({
    dataTree
  }),
  components: {
    Tree,
    TreeAddress
  },
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
body {
  background-color: #f5f6fa;
}
</style>
