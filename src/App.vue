<template>
<div>
  <h1 class="text-center mt-5">How fast can u catch me?</h1>
  <div class="d-flex justify-content-center">
    <button class="btn btn-danger m-4 pt-3 py-3 pl-5 pr-5" @click="start" :disabled="isPlaying"> Play</button>
  </div>
  
   <div v-if="isPlaying">
  <Block :delay="delay" @endGame="endGame"/>
  </div>
  <div v-if="gameEnd">
    <Result :score="score"/>
  </div>
</div>
  
</template>

<script>
import Block from "./components/Block"
import Result from "./components/Result"
export default {
 name :'App',

components:{
  Block,
  Result
},

data() { 
  return {
    isPlaying:false,
    delay:null,
    score:0,
    gameEnd:false
  }
},
methods: {
  start(){
    this.isPlaying=true;
    this.delay=2000+Math.random()*5000
  },
  endGame(score){
    this.score=score;
    this.isPlaying=false;
    this.gameEnd=true;
  }
}
}
</script>

<style>
.btn{
  text-align: center;
  align-items: center;
}
</style>