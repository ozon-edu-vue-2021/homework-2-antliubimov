<template>
  <div id="app">
    <tree :treeData="tree"></tree>
  </div>
</template>

<script>
import axios from 'axios';
import Tree from './components/Tree/Tree';

export default {
  name: 'App',
  data: () => ({
    tree: {}
  }),
  components: {
    Tree
  },
  created() {
    axios.get('./static/node_modules.json')
      .then(response => {
        this.tree = response.data
      })
      .catch(error => console.log(error))
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
body {
  background-color: #f5f6fa;
}
</style>
