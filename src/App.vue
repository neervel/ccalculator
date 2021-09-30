<template>
  <div id="app">
    <Calculator />
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style lang="sass">
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;500;600&display=swap')

  *
    color: #2c3e50
    font-family: 'Open Sans', sans-serif
    box-sizing: border-box

  body
    margin: 0
</style>

