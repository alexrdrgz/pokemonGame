/* eslint-disable no-unused-vars */
<template>
  <div id="app">
    <p class="pokeButton" @click="RunRound">Generate Random Pokemon</p>
    <p class="pokeButton">Submit</p>
    <div class="gameContent">
      <Pokemon id="Pokemon" v-bind:imgURL="imgUrl" />
      <Controller id="Controller" v-bind:options="choices" />
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
    choices: [],
    correctAnswer: '',
    name: '',
  }
  },
  components: {
    Pokemon,
    Controller
  },
  methods: {
    RunRound: function(){
      this.choices = [];
      this.SetPokemon();
      this.SetOptions();
    },
    // // Random Number Generator Used To Pick ID of Pokemon
    RandomNumber: function(){
        return (Math.floor(Math.random() * (150 - 1) + 1)).toString(10);
    },
    // API Call To Get Pokemon Data 
    ReturnPokemonName: function(id) {
        return axios.get('https://pokeapi.co/api/v2/pokemon/' + id + '/')
        .then(response => {
          return response.data.name;
        })
    },
    SetPokemon: function(){
        var id = this.RandomNumber();
        this.imgUrl = 'https://pokeres.bastionbot.org/images/pokemon/'+ id + '.png';
        this.SetCorrectAnswer(id);
    },
    //Sets var correctAnswer To The Pokemon Name
    SetCorrectAnswer: function(id){
      this.ReturnPokemonName(id).then(data => {
           this.correctAnswer = data;
           this.choices.splice(0, 1, data);
        })
    },
    SetOptions: function(){
      for (var i = 1; i < 4; i++){
        this.ReturnPokemonName(this.RandomNumber()).then(data =>{
            console.log(i + "test");
            this.choices.splice(i , 1 , data);  
            console.log(this.choices[i]);
        }) 
      }

    },
    RandomizeOptions: function(){

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
