/* eslint-disable no-unused-vars */
/* eslint-disable no-unused-vars */
/* eslint-disable no-unused-vars */

<template>
  <div>
      <div>
          <h1>Pokemon</h1>
          <p @click="ReturnRandomPokemon" class="pokeButton">Generate Random Pokemon</p>
          <img :src=imgURL>
      </div>
      <div></div>
  </div>
</template>

<script>
import axios from 'axios';

// eslint-disable-next-line no-unused-vars
const pokeUrl = 'https://pokeapi.co/api/v2/pokemon/'; 
// eslint-disable-next-line no-unused-vars
var pokeID = '10';


export default {

  name: 'Pokemon',
  props: {
    msg: String
  },
  
  mounted () {
    console.log(pokeUrl + pokeID + '/');
    axios.get(pokeUrl + pokeID  + '/',{})
      .then(function (response) {
        console.log(response );
      }) 
  },
  data: function () {
  return {
    pokeUrl: 'https://pokeapi.co/api/v2/pokemon/',
    imgURL:'',
    CorrectAnswer: '',

  }
  },

  methods: {

    // Random Number Generator Used To 
    RandomNumber: function(){
        return (Math.floor(Math.random() * (150 - 1) + 1)).toString(10);
    },
    // API Call To Get Pokemon Data 
    ReturnPokemonData: function(id) {
        axios.get('https://pokeapi.co/api/v2/pokemon/' + id + '/' ,{})
        .then(function (response) {
          console.log(response );
          this.CorrectAnswer = JSON.parse(response);
          console.log(this.CorrectAnswer);
          console.log('test 2');
          console.log(response );
        }) 
      },

    ReturnRandomPokemon: function(){

        var id = this.RandomNumber();
        this.imgURL = 'https://pokeres.bastionbot.org/images/pokemon/'+ id + '.png';
        return this.ReturnPokemonData(id);

    }
    },
    // API Call To Get Pokemon Image
    


};




</script>

<style>
  .pokeButton{
    background: #FBD743;
    padding: 4px;
    width: 50%;
    margin-left: 25%;
    border-radius: 8px;
  }
</style>