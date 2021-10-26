<template>
  <div  @click="toggleDirectory" :class="['tree-item',{'bold': isOpen}]">
    <img v-if="isOpen" src="../../assets/folder-open.svg" width="16" height="16" alt="directory">
    <img v-else src="../../assets/folder-close.svg" width="16" height="16" alt="directory">
    {{ TreeItemData.name }}
  </div>
</template>

<script>
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
    }
  }
}
</script>

<style scoped>
  .bold {
    font-weight: bold;
  }
</style>