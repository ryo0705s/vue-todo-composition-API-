<template>
  <div id="app">
    {{ state.message }}
  </div>
</template>

<script>
import { reactive } from "vue";
export default {
  setup() {
    const state = reactive({
      message: "Hello Wold",
    });
    return {
      state,
    };
  },
};
</script>
