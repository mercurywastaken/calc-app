<template>
  <img alt="Vue logo" class="top-0 w-100" src="./assets/Notificationtray.png">
  <CalculatorApp/>
</template>

<script>
import CalculatorApp from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    CalculatorApp
  }
}
</script>

<style>
#app {
  font-family: Arial, 'Lucida Grande', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #fff;
}
</style>
