<template>
  <div id="app">
    <ul>
    <li @click="id = 0"><a href="#Congruence">Congruence Modulaire</li>
    <li @click="id = 1"><a href="#PGDC" target="_self">PGDC</a></li>
    <li @click="id = 2"><a href="#Inverse">Inverse modulaire</a></li>
  </ul>
  </div>
  <Textepgdc v-else-if="id === 0">
    <Textecongruence v-else-if="id === 1">
    
    <Texteinverse v-else="id === 2">
</template>

<script>
import Textecongruence from './components/Partie_1/TexteModulo.vue'
import Textepgdc from './components/Partie_2/Textepgdc.vue'
import Texteinverse from './components/Partie_3/Texteinverse.vue'

export default {
  name: 'App',
  components: {
    Textecongruence,
    Textepgdc,
    Texteinverse,
  },
  data() {
    return {
      id: 0
    };
  },
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
body {
  margin:0;
  background: #282828
}

ul {
  display: flex;
  justify-content: space-evenly;
  list-style-type: none;
  margin: 0;
  padding: 0;
  background-color: #1F2833;
  position: fixed;
  top: 0;
  width: 100%;
}

li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li a:hover {
  background-color: #C5C6C7;
  color: #3500D3;
}
</style>
