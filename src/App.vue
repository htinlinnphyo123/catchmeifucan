<template>
  <h1>How fast can you catch me</h1>
  <button class="playbtn" @click="play" :disabled="isPlaying">Play</button>
  <div v-if="isPlaying">
    <Block :delay="delay" @stopTimer="stopTimer"/>
  </div>
  <div v-if="showResult">
    <Result :score="score"/>
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from './components/Result.vue';
export default {
  data(){
    return {
      isPlaying : false,
      delay : null,
      showResult : false,
      score : 0
    }
  },
  components : {
    Block,
    Result
  },
  methods : {
    play(){
      this.isPlaying = true;
      this.delay = 2000+Math.random()*5000;
      // console.log(this.delay);
    },
    stopTimer(score){
      // console.log(score);
      this.isPlaying = false;
      this.showResult = true;
      this.score = score;
    }
  }
}
</script>

<style>
  body{
    text-align:center;
    margin-top:60px;
  }
  .playbtn{
    padding:10px 20px;
    background-color:black;
    color:#fff;
    border:none;
    cursor:pointer;
    border-radius:5px;
  }
  .playbtn:active{
    transform:scale(0.8);
  }
  .playbtn:disabled{
    opacity:0.65;
    cursor:not-allowed;
  }

</style>