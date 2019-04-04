<template>
  <div id="app">
    <h1>Literally just a calculator</h1>
    <Calculator/>
    <p>Made by: <a target="_blank" href="https://benjaminhoppe.co/">Benjamin Hoppe</a></p>
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
  color: white;
  margin-top: 60px;
}

h1 {
  text-align: center;
  font-size: 30px;
}

p {
  text-align: center;
}

a {
  text-decoration: none;
  color: #3ADBC4;
  transition: opacity 0.3s;
  opacity: 1;
}

p > a:hover {
  transition: opacity 0.3s;
  opacity: 0.5;


}
</style>
