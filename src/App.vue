<template>
  <div id="app">
    <HomeComponent></HomeComponent>
  </div>
</template>

<script>
import HomeComponent from './components/HomeComponent'

export default {
  name: 'app',
  components: {
    HomeComponent
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 10px;
}
</style>
