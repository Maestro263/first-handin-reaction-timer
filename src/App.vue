<template>
<h1>My Reaction Timer</h1>
<button @click="begin" :disabled="isPlaying">Begin the Game</button>
<block v-if="isPlaying" :delay="delay" @end="gameOver"/>
<results v-if="showResults" :score="score" />
</template>

<script>
import block from './components/block.vue'
import results from './components/results.vue'

export default {
  name: 'App',
  components: { block, results },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    begin(){
      //Between 2-7 seconds
      this.delay = 2000 + Math.random() * 5000,
      this.isPlaying = true
      this.showResults = false
    },
    gameOver(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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
  color: teal;
  margin-top: 60px;
}
*{
  background: yellow;
}
button{
  background: blue;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
