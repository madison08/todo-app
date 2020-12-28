<template>
  <div id="app">
    <div id="app-container">
      <container>
      </container>
      <list></list>
    </div>
  </div>
</template>

<script>
import Container from './components/Container.vue'
import List from './components/List.vue'

export default {
  name: 'App',
  components: {
    'container': Container,
    'list' : List
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 40px;
}
</style>
