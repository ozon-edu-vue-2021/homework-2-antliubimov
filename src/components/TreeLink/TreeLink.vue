<template>
  <div class="tree-link">
    <img src="../../assets/link.svg" width="16" height="16">
    {{ TreeItem.name }}
  </div>
</template>

<script>
export default {
  name: "TreeLink",
  props: {
    TreeItem: Object
  }
}
</script>

<style scoped>

</style>