<template>
  <div id="app">
    <nav>
      <router-link to="/" >Home</router-link>
      <router-link to="/about" >About</router-link>
      <router-view></router-view>
    </nav>
  </div>
</template>

<script>
import Skills from './components/Skills.vue'

export default {
  name: 'app',
  components: {
    Skills
  }
}
</script>

<style>
body{
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  align-items: center;
  margin: 0;
background: #2c3e50;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #ffff;
  margin-top: 60px;
  width: 50%;
}
nav{
  padding: 20px
}
nav a{
  background: #ffff;
  padding: 10px;
  text-decoration: none;
  color: blue;
  border-radius: 5px;
  margin-right: 30px;
}
</style>
