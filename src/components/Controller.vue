<template>
  <div>
      <h1>Controller</h1>
      <div class="buttonContainer">
        <p><img id="upArrow" src="../assets/arrowKey.png"/> Charzard</p>
        <p><img id="rightArrow" src="../assets/arrowKey.png"/> Bulbasaur</p>
        <p><img id="downArrow" src="../assets/arrowKey.png"/> Ivysaur</p>
        <p><img id="leftArrow" src="../assets/arrowKey.png"/> Pikachu</p>
      </div>
  </div> 
</template>

<script>
export default {

}
</script>

<style>
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