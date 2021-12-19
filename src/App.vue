<template>
  <h1>Reaction timer ...</h1>

  <Block v-if="isPalying" :delay="delay" @end="endGame" />
  <Result v-if="showResults" :score="score" />
  <button @click="start" :disabled="isPalying">Play</button>
  <!-- <p v-if="showResults">Reaction Time {{ score }} ms</p> -->
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    Block,
    Result,
  },
  data() {
    return {
      isPalying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + 5000 * Math.random();
      this.isPalying = true;
      console.log(this.isPalying);
      console.log(this.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPalying = false;
      this.showResults = true
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
