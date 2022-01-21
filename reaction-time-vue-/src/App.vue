<template>
  <h1>Muneeb Reaction Timer</h1>
  <button @click="start" :disabled="isPLaying">play</button>
  <Block v-if="isPLaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"


export default {
  name: 'App',
  components: { Block, Results },
  data(){
    return{
      isPLaying:false,
      delay:null,
      score:null,
      showResults: false
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000 
      this.isPLaying = true
    
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPLaying = false
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
  background:violet ;
  color: #444;
  border: none;
  padding: 8px 16px;
  border-radius:4px ;
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
