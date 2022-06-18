<template>
  <div v-if="showBlock" class="block" @click="stopTimer()">Block</div>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";

export default defineComponent({
  props: {
    delay: {
      type: Number,
      required: true,
      nullable: true,
    },
  },

  setup(props, { emit }) {
    const showBlock = ref(false);
    const reactionTime = ref(0);
    let timer: number;

    onMounted(() =>
      setTimeout(() => {
        showBlock.value = true;
        startTimer();
      }, props.delay)
    );

    const startTimer = () => {
      timer = setInterval(() => {
        reactionTime.value += 10;
      }, 10);
    };

    const stopTimer = () => {
      clearInterval(timer);
      emit("end", reactionTime.value);
    };

    return {
      showBlock,
      stopTimer,
    };
  },
});
</script>

<style scoped>
.block {
  margin: 40px auto;
  background: rgb(26, 182, 148);
  width: 400px;
  padding: 100px 0;
  text-align: center;
  color: white;
  border-radius: 0.5rem;
}
</style>
