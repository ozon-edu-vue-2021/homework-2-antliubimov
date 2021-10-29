<template>
  <p class="address"><span>Address: </span> {{ address }}</p>
</template>

<script>
import { bus } from '../../main';

export default {
  name: "TreeAddress",
  data() {
    return {
      address: ''
    }
  },
  created() {
    bus.$on('addressShow', (res) => this.address = res)
  },
}

</script>

<style scoped>
  .address {
    text-align: left;
    margin-left: 20px;
  }
  .address span {
    font-weight: bold;
  }
</style>