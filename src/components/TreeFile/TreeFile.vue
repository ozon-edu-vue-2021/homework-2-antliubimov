<template>
  <div @click="highlight" :class="['tree-file', {'highlight': isActive}]">
    <img src="../../assets/file.svg" width="16" height="16">
    {{ TreeItem.name }}
  </div>
</template>

<script>
export default {
  name: "TreeFile",
  props: {
    TreeItem: Object
  },
  data() {
    return {
      isActive: false
    }
  },
  methods: {
    highlight() {
      this.isActive = !this.isActive
    }
  }
}
</script>

<style scoped>
  .highlight {
    background-color: #0611d642;
    border-radius: 5px;
  }
</style>