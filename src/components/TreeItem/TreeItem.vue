<template>
  <li class="tree__item">
    <tree-directory v-if="isDirectory" :TreeItemData="TreeItemData" @toggle="onToggle"></tree-directory>
    <tree-file v-else-if="isFile" :TreeItemData="TreeItemData"></tree-file>
    <tree-link v-else-if="isLink" :TreeItemData="TreeItemData"></tree-link>


    <ul v-show="isOpen" v-if="isDirectory" class="tree__list">
      <tree-item v-for="(elem, index) in TreeItemData['contents']" :TreeItemData="elem" :key="index"></tree-item>
    </ul>
  </li>
</template>

<script>
import TreeDirectory from "../TreeDirectory/TreeDirectory";
import TreeFile from '../TreeFile/TreeFile';
import TreeLink from '../TreeLink/TreeLink';

export default {
  name: "tree-item",
  props: {
    TreeItemData: Object,
  },
  data() {
    return {
      isOpen: false,
    }
  },
  computed: {
    isDirectory() {
      return this.TreeItemData.type === 'directory'
    },
    isFile() {
      return this.TreeItemData.type === 'file'
    },
    isLink() {
      return this.TreeItemData.type === 'link'
    },
  },
  methods: {
    onToggle(isToogle) {
      this.isOpen = isToogle;
    }
  },
  components: {
    TreeDirectory,
    TreeFile,
    TreeLink,
  }
}
</script>

<style scoped>
  .tree__list {
    padding-left: 20px;
  }

  .tree__item {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin: 6px 0;
    cursor: pointer;
  }
</style>