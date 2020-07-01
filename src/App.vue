/* eslint-disable no-unused-vars */
<template>
  <div id="app">
    <div class="gameContent">
      <Pokemon id="Pokemon"/>
      
      <Controller id="Controller"/>
    </div>
  </div>
</template>

<script>

import Pokemon from './components/Pokemon.vue'
import Controller from './components/Controller'

export default {
  name: 'App',
  components: {
    Pokemon,
    Controller
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
.gameContent{
  padding: 6%;
   display: flex;
  justify-content: center;
  align-items: center;
}

#Controller{
  border: solid 3px #FBD743;
  background: #5EB9FF;
  width: 100%;
  height: 600px;
}
#Pokemon{
  border: solid 3px #FBD743;
  background: white;
  width: 100%;
  height: 600px;
}


</style>
