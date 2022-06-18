<template>
  <h1>Reaction Timer</h1>
  <button @click="startGame" :disabled="isPlaying">Start Game</button>
  <BlockComp v-if="isPlaying" :delay="delay" @end="endGame" />
  <ResultsComp v-if="showResults" :score="score" />
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import BlockComp from "./components/Block-comp.vue";
import ResultsComp from "./components/Results-comp.vue";

export default defineComponent({
  name: "App",
  components: { BlockComp, ResultsComp },
  setup() {
    const isPlaying = ref(false);
    const delay = ref(0);
    const score = ref(0);
    const showResults = ref(false);

    const startGame = () => {
      isPlaying.value = true;
      delay.value = 2000 + Math.random() * 5000;
      showResults.value = false;
    };

    const endGame = (reactionTime: number) => {
      score.value = reactionTime;
      isPlaying.value = false;
      showResults.value = true;
    };

    return { isPlaying, delay, startGame, endGame, score, showResults };
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}

button {
  all: unset;
  background: rgb(21, 145, 161);
  padding: 1rem;
  color: white;
  border-radius: 0.3rem;
  cursor: pointer;
}

button:hover {
  background: rgb(12, 98, 109);
}

button:disabled,
button[disabled] {
  background-color: rgb(25, 41, 46);
  color: white;
}
</style>
