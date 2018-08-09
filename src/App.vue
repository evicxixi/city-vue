<template>
  <div id="app">

    <LHeader/>

    <router-view/>

    <LFooter/>


  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.min.css'
  import LHeader from './components/Head'
  import LFooter from './components/Foot'

  export default {
    name: 'App',
    components: {
      LHeader,
      LFooter
    }
  }
</script>

<style>
  body {
    margin: 0;
  }
  *:not([class*="icon"]):not(i):not(pre):not(code):not(kbd):not(samp):not(var ) {
    font-family: "Microsoft Yahei" !important;
    text-shadow: 0.05em 0.05em 0.2em #999999 !important;
  }
</style>
