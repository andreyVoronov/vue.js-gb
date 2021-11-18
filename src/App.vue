<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <calculator />
    <Calc />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import calculator from './components/calculator.vue'
import Calc from './components/calc.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    calculator,
    Calc
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
