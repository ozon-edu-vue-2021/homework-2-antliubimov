<template>
    <img :src="computedSrc" :alt="`${type}`" width="16" height="16">
</template>

<script>
export default {
  name: "TreeIcon",
  props: {
    type: String,
    open: Boolean,
  },
  computed: {
    computedSrc() {
      return this.isDirectory ? this.isOpenDirectory : require(`../../assets/${this.type}.svg`)
    },
    isDirectory() {
      return this.type === 'directory'
    },
    isOpenDirectory() {
      return this.open ? require(`../../assets/${this.type}-open.svg`) : require(`../../assets/${this.type}-close.svg`)
    }
  }
}
</script>

<style scoped>

</style>