<template>
  <h1>reaction timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <MainBlock v-if="isPlaying" :delay="delay" @closeBlock="closeBlock" />
  <ResultBlock
    v-if="!isPlaying && gameStarted"
    :reactionTime="reactionTime"
  />
</template>

<script>
import MainBlock from "./components/MainBlock.vue";
import ResultBlock from "./components/ResultBlock.vue";

export default {
  name: "App",
  components: {
    MainBlock,
    ResultBlock,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: 0,
      gameStarted: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = !this.isPlaying;
      this.delay = 1000 + Math.random() * 5000;
      this.gameStarted = true;
    },
    closeBlock({ reactionTime }) {
      console.log("close block is fired");
      this.isPlaying = false;
      this.reactionTime = reactionTime;
    },
  },
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
button{
  background-color: #0faf87;
  color:white;
  border:none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor:not-allowed;
}
</style>
