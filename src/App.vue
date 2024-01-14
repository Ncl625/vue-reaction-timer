<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <MyBlock v-if="isPlaying" :delay="delay" @end="endGame" />
  <TestResults v-if="showResults" :score="score" />
  <!-- <p v-if="showResults">Reaction Time: {{ score }}ms</p> -->
</template>

<script>
import MyBlock from './components/MyBlock.vue'
import TestResults from './components/TestResults.vue'

export default {
  name: 'App',
  components: { MyBlock, TestResults },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start (){
      this.delay= 2000 + Math.random()*5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime){
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
  color: #444;
  margin-top: 60px;
}
button{
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16 px;
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
