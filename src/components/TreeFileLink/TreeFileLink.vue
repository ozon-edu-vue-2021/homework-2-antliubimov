<template>
  <div @click="highlight"
       :class="computedClasses">
    <tree-icon :type="TreeItemData.type"/>
    {{ TreeItemData.name }}
  </div>
</template>

<script>
import TreeIcon from '../TreeIcon/TreeIcon';
import {bus} from "../../main";

export default {
  name: "TreeFileLink",
  props: {
    TreeItemData: Object
  },
  data() {
    return {
      isActive: false
    }
  },
  computed: {
    computedClasses() {
      return this.isActive ? `tree-${this.TreeItemData.type} highlight highlight-${this.TreeItemData.type}` :
          `tree-${this.TreeItemData.type}`
    }
  },
  methods: {
    highlight() {
      this.isActive = !this.isActive;

      let elem = this.$parent;
      let res = [];
      while (elem.$options.propsData.TreeItemData !== undefined) {
        res.push(elem.$options.propsData.TreeItemData.name);
        elem = elem.$parent;
      }
      bus.$emit('addressShow', '/'+res.reverse().join('/'));
    }
  },
  components: {
    TreeIcon
  }
}
</script>

<style scoped>
  .tree-file {
    color: #2f8716ff;
  }
  .tree-link {
    color: #010f93;
  }
  .highlight {
    border-radius: 5px;
  }
  .highlight-file {
    background-color: #0611d642;
  }
  .highlight-link {
    background-color: #99c794ff;
  }
</style>