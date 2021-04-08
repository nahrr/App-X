<template>
  <div class="count">
    <button @click="increment">Count is: {{state.count}}, double is: {{state.double}}</button>
  </div>
</template>

<script>
import { reactive, computed } from "vue";

export default {
  name: "Count",

  setup() {
    const state = reactive({
      count: 0,
      double: computed(() => state.count * 2)
    });

    const increment = () => state.count++;

    return {
      state,
      increment
    };
  }
};
</script>