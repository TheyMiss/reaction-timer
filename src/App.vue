<template>
  <h1>Reaction Timer</h1>
  <button @click="startGame()" :disabled="isPlaying">Start Game</button>
  <BlockComp v-if="isPlaying" :delay="delay" />
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import BlockComp from "./components/Block-comp.vue";

export default defineComponent({
  name: "App",
  components: { BlockComp },
  setup() {
    const isPlaying = ref(false);
    const delay = ref<null | number>(null);

    const startGame = () => {
      isPlaying.value = true;
      delay.value = 2000 + Math.random() * 5000;
    };

    return { isPlaying, delay, startGame };
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
