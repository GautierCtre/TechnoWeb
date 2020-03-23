<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/HS.png">
    <HearthStoneCards />
  </div>
</template>

<script>
import HearthStoneCards from './components/HearthStoneCards.vue'

export default {
  name: 'App',
  components: {
    HearthStoneCards
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
