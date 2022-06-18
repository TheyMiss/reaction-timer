<template>
  <p>Reacttion time: {{ score }} ms</p>
  <p>Summary: {{ summary }}</p>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";

export default defineComponent({
  props: {
    score: {
      type: Number,
      required: true,
    },
  },
  setup(props) {
    const summary = ref("");

    onMounted(() => {
      if (props.score < 250) {
        summary.value = "Super fast!";
      } else if (props.score < 500) {
        summary.value = "Very fast!";
      } else if (props.score < 800) {
        summary.value = "Fast!";
      } else if (props.score < 1000) {
        summary.value = "Normal speed!";
      } else if (props.score < 1200) {
        summary.value = "Slow speed!";
      } else {
        summary.value = "You are a snail!";
      }
    });
    return {
      summary,
    };
  },
});
</script>
