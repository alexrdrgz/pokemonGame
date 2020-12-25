/* eslint-disable no-unused-vars */

<template>
  <div>
      <div>
          <h1 class="title">Pokemon</h1>
          <img class="pokemonPic"  :src="imgURL">
      </div>
      <div></div>
  </div>
</template>

<script>




export default {

  name: 'Pokemon',
  props: {
    imgURL: String
  },
  
  mounted () {
   
  },
  data: function () {
  return {
  
    imgUrl:'',
 
  }
  },
  methods: {
    },
    
    
};

</script>

<style>
  .title{
    text-align: center;
  }
  .pokeButton{
    background: #FBD743;
    padding: 4px;
    width: 50%;
    margin-left: 25%;
    border-radius: 8px;
  }
  .pokemonPic{
    width: 50%;
    margin:10px;
    margin-left: 25%;
  }

  .pokeImg{
    -webkit-filter: contrast(0) sepia(100%) hue-rotate(190deg) saturate(2000%) brightness(100%);
    filter: contrast(0) sepia(100%) hue-rotate(190deg) saturate(2000%) brightness(100%);
    opacity: 1;
  }
</style>