<template>
  <div id="app">
    <CountDown date="2017-03-20 12:00"></CountDown>
    <CountDown date="2017-03-21 12:00"></CountDown>
    <CountDown date="2017-03-22 12:00"></CountDown>
  </div>
</template>

<script>
import CountDown from './components/CountDown'
export default {
  name: 'app',
  components: {
    CountDown
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
