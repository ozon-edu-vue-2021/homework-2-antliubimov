<template>
  <div class="tree">
    <ul class="tree__list">
      <tree-item :TreeItemData="treeData"/>
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