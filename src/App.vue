<template>
  <img alt="Vue logo" style="width: 414px" class="top-0" src="./assets/Notificationtray.png">
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
