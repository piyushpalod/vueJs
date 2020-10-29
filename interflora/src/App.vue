<template>
  <img alt="Vue logo" src="./assets/logo.svg" style="height: 96px; width:96px">
  <greetingCard msg=" "/>
</template>

<script>
import greetingCard from './components/card.vue'

export default {
  name: 'App',
  components: {
    greetingCard
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
