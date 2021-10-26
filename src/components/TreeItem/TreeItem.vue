<template>
  <li class="tree__item">
    <div  v-if="isDirectory" @click="toggle" :class="['tree-item',{'bold': isOpen}]">
      <img v-if="isOpen" src="../../assets/folder-open.svg" width="16" height="16" alt="directory">
      <img v-else src="../../assets/folder-close.svg" width="16" height="16" alt="directory">
      {{ TreeItemData.name }}
    </div>
    <tree-file v-else-if="isFile" :TreeItemData="TreeItemData"></tree-file>
    <tree-link v-else-if="isLink" :TreeItemData="TreeItemData"></tree-link>


    <ul v-show="isOpen" v-if="isDirectory" class="tree__list">
      <tree-item v-for="(elem, index) in TreeItemData['contents']" :TreeItemData="elem" :key="index"></tree-item>
    </ul>
  </li>
</template>

<script>

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
    toggle() {
      this.isOpen = !this.isOpen;
    }
  },
  components: {
    TreeFile,
    TreeLink,
  }
}
</script>

<style scoped>
  .tree__list {
    padding-left: 20px;
  }

  .bold {
    font-weight: bold;
  }

  .tree__item {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin: 6px 0;
    cursor: pointer;
  }
</style>