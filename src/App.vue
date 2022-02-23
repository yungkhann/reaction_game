<template>
  <h1>Reaction Game</h1>
  <button class="play" @click="start" :disabled="isPlaying">PLAY</button>
  <block v-if="isPlaying" :delay="delay" @stopTimer="endGame"></block>
  <results :score="score" v-if="showResult"></results>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:null,
      showResult:false

    }
  },
  components: {
    Block,
    Results
  },
  methods:{
    start(){
      this.delay = 500 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
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
.play{
  width:100px;
  border-radius: 5px;
  border: none;
  background: #2c3e50;
  color:white;
  text-align: center;
  padding: 10px 0;
  margin: 40px auto;
}
.play:disabled{
    background: gray;

}

</style>
