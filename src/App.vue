<template>
  
  <h1>Reaction Timer Game</h1>
  <button @click="start" :disabled="isPlaying"  > Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <Result v-if="showResult" :score="score"></Result>
</template>

<script>
import Block from '@/components/Block'
import Result from '@/components/Result'
export default {
  name: 'App',
  components: {
    Block, Result   
  },
  data(){
    return{
      delay:null,
      isPlaying: false,
      score:null,
      showResult:false,

    }
  },
  methods:{
    start(){
     this.isPlaying =true
     this.delay = 2000 + Math.random()  * 5000
     this.showResult =false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    } 
 
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
button{
  padding: 8px 16px;
  background: rgb(51, 228, 235);
  border-radius:4px;
  border: none;
  color: #fff;
  cursor: pointer;
}
button[disabled]{
  background:#ddd;
  cursor: not-allowed;
}
</style>
