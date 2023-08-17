<template>
  <div>
    <h1>Reaction Timer Game</h1>
    <p v-if="showResults">Reaction time: {{ reactionTime }} ms</p>
    <button @click="startGame" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying"  :delay="delay"  @end="endGame"/>
  </div>
</template>

<script>
import Block from './components/Block.vue'

export default {
  components:{ Block },
  data(){
    return{
      isPlaying:false,
      delay:null,
      reactionTime:0,
      showResults: false
    }
  },
  methods:{
    startGame(){
      this.isPlaying= true
      this.showResults = false
      this.delay = 1000 + Math.random() * 5000
    },
    endGame(time){
      this.reactionTime= time
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
#app {
  display: block;
    /* display: flex; */
    /* flex-direction: row; */
  
}
</style>
