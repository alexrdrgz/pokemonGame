/* eslint-disable no-unused-vars */
<template>
  <div id="app">
    <p class="pokeButton" @click="SetPokemon">Generate Random Pokemon</p>
    <p class="pokeButton">Submit</p>
    <div class="gameContent">
      <Pokemon id="Pokemon" :imgURL="imgUrl" />
      <Controller id="Controller" :options="choices" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Pokemon from './components/Pokemon.vue'
import Controller from './components/Controller'

export default {
  name: 'App',
  props: {
   pokemon: String,
   id: Number,
   options: Array,
   score: Number,
   selected: String,
   imageURL:String

 },
 data: function () {
  return {
    imgUrl:'',
    choices: ['hello','test','check','yee'],
    correctAnswer: 'pikachu',
    name: ''
  }
  },
  components: {
    Pokemon,
    Controller
  },
  methods: {
    // // Random Number Generator Used To Pick ID of Pokemon
    RandomNumber: function(){
        return (Math.floor(Math.random() * (150 - 1) + 1)).toString(10);
    },
    // API Call To Get Pokemon Data 
    ReturnPokemonName: function(id) {
        
        axios.get('https://pokeapi.co/api/v2/pokemon/' + id + '/' ,{})
        .then((response) => {
         this.name = response.data.name;
        }) 
        return this.name;
      },
    SetCorrectAnswer: function(id){
      console.log(this.ReturnPokemonName(id));
      this.correctAnswer = this.ReturnPokemonName(id);
      console.log(this.correctAnswer + 'hey');
      return 'hello';
    },
    //Sets Correct Answer To The Pokemon Name
    SetPokemon: function(){
        var id = this.RandomNumber();
        this.imgUrl = 'https://pokeres.bastionbot.org/images/pokemon/'+ id + '.png';
        return this.SetCorrectAnswer(id);
    },
    checkAnswer: function(){
      if(this.selected === this.correctAnswer){
        return true;
      } else {
        return false;
      }
    }

    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
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
