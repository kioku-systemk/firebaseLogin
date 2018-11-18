<template>
  <div id="app">
    <img src="./assets/logo.png">
    <authtest/>
    <FirebaseAuth/>
  </div>
</template>

<script>
import authtest from './components/authtest'
import FirebaseAuth from './components/FirebaseAuth'

export default {
  name: 'App',
  components: {
    authtest,
    FirebaseAuth
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
