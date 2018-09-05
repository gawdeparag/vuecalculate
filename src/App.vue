<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" style="height:150px;">
    <h3>Vue Calculator</h3>
    <h4>A basic calculator powered by Vue.js</h4>
    <Calculator/>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'app',
  components: {
    Calculator
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
