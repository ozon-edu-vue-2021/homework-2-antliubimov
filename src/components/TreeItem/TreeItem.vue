<template>
  <li class="tree__item">
    <div v-if="isDirectory" >
      <div @click="toggle" :class="['tree-link',{'bold': isOpen}]">
        <img v-if="isOpen" src="../../assets/folder-open.svg" width="16" height="16">
        <img v-else src="../../assets/folder-close.svg" width="16" height="16">
        {{ TreeItem.name }}
      </div>
    </div>
    <div v-else-if="isFile">
      <tree-file :TreeItem="TreeItem"></tree-file>
    </div>
    <div v-else-if="isLink">
      <tree-link :TreeItem="TreeItem"></tree-link>
    </div>

    <ul v-show="isOpen" v-if="isDirectory" class="tree__list">
      <tree-item v-for="(elem, index) in TreeItem.contents" :TreeItem="elem" :key="index"></tree-item>
    </ul>
  </li>
</template>

<script>
import TreeFile from '../TreeFile/TreeFile';
import TreeLink from '../TreeLink/TreeLink';

export default {
  name: "tree-item",
  props: {
    TreeItem: Object
  },
  data() {
    return {
      isOpen: false,
    }
  },
  computed: {
    isDirectory() {
      return this.TreeItem.type === 'directory'
    },
    isFile() {
      return this.TreeItem.type === 'file'
    },
    isLink() {
      return this.TreeItem.type === 'link'
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