<template>
  <div class="block">Block</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    delay: {
      validator: (props) => typeof props === "string" || props === null,
      required: false,
    },
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
