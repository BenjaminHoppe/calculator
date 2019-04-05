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
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vw;
}

h1 {
  text-align: center;
  font-size: 30px;
  font-family: 'Montserrat', sans-serif;
}

p {
  text-align: center;
  font-family: 'Montserrat', sans-serif;
}

a {
  font-family: 'Montserrat', sans-serif;
  text-decoration: none;
  color: #3ADBC4;
  transition: opacity 0.3s;
  opacity: 1;
}

p > a:hover {
  transition: opacity 0.3s;
  opacity: 0.5;
}

@import url('https://fonts.googleapis.com/css?family=Montserrat:200');
</style>
