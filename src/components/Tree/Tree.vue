<template>
  <div class="tree">
    <ul class="tree__list">
      <tree-item :TreeItem="treeData"></tree-item>
    </ul>
  </div>
</template>

<script>
import TreeItem from '../TreeItem/TreeItem';

export default {
  name: 'Tree',
  props: {
    treeData: Object
  },
  components: {
    TreeItem
  }
}
</script>

<style scoped>
  .tree__list {
    padding-left: 20px;
  }
</style>