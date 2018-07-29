<template>
  <div id="app">
     <Egg></Egg>
  </div>
</template>

<script>
import Egg from "@/components/egg"
export default {
  name: 'App',
  components: {
    Egg
  }
}
</script>

<style lang="scss">
  @import "@/style/reset.scss";
  @import "@/style/common.scss";
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  height: 100%;
}
</style>
