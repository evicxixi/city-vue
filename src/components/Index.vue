<template>
  <div>
    <h1>{{msg}}</h1>
    <img v-bind:src="img" alt="">
  </div>
</template>

<script>
  export default {
    name: "index",
    data() {
      return {
        msg: '这是首页',
        img: 'static/img/logo.png'
      }
    }
  }
</script>

<style scoped>

</style>
