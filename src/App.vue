<template>
  <div id="app">
    <NumberRoll :number="123321"  :background="'#ccc'" :isSemicolon="false" />
  </div>
</template>

<script>
import NumberRoll from "./Plugin.vue"
export default {
  name: 'App',
  components: {
    NumberRoll
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
