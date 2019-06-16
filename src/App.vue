<template>
  <div id="app">
    <MillerRabinPrimalityTest/>
  </div>
</template>

<script>
import MillerRabinPrimalityTest from './components/MillerRabinPrimalityTest.vue'

export default {
  name: 'app',
  components: {
    MillerRabinPrimalityTest
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
