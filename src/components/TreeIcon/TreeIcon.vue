<template>
  <div @click="highlight" :class="['tree-link', {'highlight': isActive}]">
    <img src="../../assets/link.svg" width="16" height="16" alt="link">
    {{ TreeItemData.name }}
  </div>
</template>

<script>
export default {
  name: "TreeLink",
  props: {
    TreeItemData: Object
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

</style>