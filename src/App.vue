<template>
  <div>   
    <h1>Ninja Reaction Timer</h1>
    <button @click="start" :disabled ="isPlaying" style="width: 300px;">Play</button>
    <Block v-if="isPlaying" :delay="delay" @update:reactionTime="stopGame"/>  
    <Results :score="score" v-if="showResults"/>
  </div>
</template>

<script setup>
import Block from './components/block.vue'
import Results from './components/results.vue'
import { ref } from "vue"

const isPlaying = ref(false);

const score = ref()

const delay = ref();

const showResults = ref(false)

const start = () => {
  delay.value = 2000 + Math.random() * 5000;
  isPlaying.value = true;

}

const stopGame = (reactionTime) => {
  score.value = reactionTime
  isPlaying.value = false
  showResults.value = true
};

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
</style>
