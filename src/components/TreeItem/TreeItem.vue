<template>
  <li class="tree__item">
    <tree-directory v-if="isDirectory" :TreeItemData="TreeItemData" @toggle="onToggle"/>
    <tree-file-link v-else-if="isFileLink" :TreeItemData="TreeItemData"/>

    <ul v-show="isOpen" v-if="isDirectory" class="tree__list">
      <tree-item v-for="(elem, index) in TreeItemData['contents']" :TreeItemData="elem" :key="index"/>
    </ul>
  </li>
</template>

<script>
import TreeDirectory from "../TreeDirectory/TreeDirectory";
import TreeFileLink from '../TreeFileLink/TreeFileLink';

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
    isFileLink() {
      return this.TreeItemData.type === 'file' || this.TreeItemData.type === 'link'
    },
  },
  methods: {
    onToggle(isToogle) {
      this.isOpen = isToogle;
    },
  },
  components: {
    TreeDirectory,
    TreeFileLink,
  },
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