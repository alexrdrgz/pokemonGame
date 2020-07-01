<template>
  <div class="ControllerContainer">
      <h1 class="title">Controller</h1>
      <div class="buttonContainer">
        <p class="option"><img id="upArrow" src="../assets/arrowKey.png"/> {{options[0]}}</p>
        <p class="option"><img id="rightArrow" src="../assets/arrowKey.png"/>{{options[1]}}</p>
        <p class="option"><img id="downArrow" src="../assets/arrowKey.png"/> {{options[2]}}</p>
        <p class="option"><img id="leftArrow" src="../assets/arrowKey.png"/> {{options[3]}}</p>
      </div>
  </div> 
</template>

<script>
export default {
  props: {
    options: Array
  },

}
</script>

<style>
  
  .buttonContainer{
    padding: 5%;
  }
  .title{
    text-align: center;
  }
  .option{
    font-size: 20px;
    
  }
  #upArrow{
    width: 15px;
    margin-right: 5px;
    transform: rotate(270deg);
  }
  #rightArrow{
    width: 15px;
    margin-right: 5px;
  }
  #downArrow{
    width: 15px;
    transform: rotate(90deg);
    margin-right: 5px;
  }
  #leftArrow{
    width: 15px;
    transform: rotate(180deg);
    margin-right: 5px;
  }
</style>