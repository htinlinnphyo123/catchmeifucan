<template>
  <div v-if="showBlock">
    <div class="block" @click="stopTimer">Click here {{ delay }}</div>
  </div>
</template>

<script>

export default {
  data(){
    return {
      showBlock : false,
      timeInterval : null,
      score : 0
    }
  },
  props : ['delay'],
  mounted(){
    setTimeout(()=>{
      this.showBlock = true;
      this.startTimer();
    },this.delay)
  },
  methods : {
    startTimer(){
      this.timeInterval = setInterval(() => {
        this.score+=50;
        // console.log(this.score);
      },50);
    },
    stopTimer(){
      clearInterval(this.timeInterval);
      this.$emit('stopTimer',this.score)
    }
  }
}
</script>

<style>
    .block{
        width:500px;
        height:300px;
        margin:20px auto;
        padding:20px;
        background-color:aqua;
        border-radius:10px;
    }
</style>