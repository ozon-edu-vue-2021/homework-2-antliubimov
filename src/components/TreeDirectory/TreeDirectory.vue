<template>
  <div  @click="toggleDirectory" :class="['tree-item',{'bold': isOpen}]">
    <tree-icon :type="TreeItemData.type" :open="isOpen"/>
    {{ TreeItemData.name }}
  </div>
</template>

<script>
import { bus } from '../../main';
import TreeIcon from "../TreeIcon/TreeIcon";

export default {
  name: "TreeDirectory",
  data() {
    return {
      isOpen: false,
    }
  },
  props: {
    TreeItemData: Object,
  },
  methods: {
    toggleDirectory() {
      this.isOpen = !this.isOpen;
      this.$emit('toggle', this.isOpen);

      let elem = this.$parent;
      let res = [];
      while (elem.$options.propsData.TreeItemData !== undefined) {
        res.push(elem.$options.propsData.TreeItemData.name);
        elem = elem.$parent;
      }
      bus.$emit('addressShow', '/'+res.reverse().join('/'));
    },
  },
  components: {
    TreeIcon,
  }
}
</script>

<style scoped>
  .bold {
    font-weight: bold;
  }
</style>