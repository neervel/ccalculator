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
  
  input
    width: 100px
    display: inline-block
    padding: 0
    margin: 0
    border: none
    border-bottom: 1px solid #000
    margin: 0 15px
    padding: 5px 10px
    font-size: 18px
    &:focus
      outline: none
</style>

