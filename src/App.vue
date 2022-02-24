<template>
  <div id="app">
    {{ message }}
    <!-- {{ state.message }} -->
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const message = ref("Hello World");
    // const state = reactive({
    //   message: "Hello Wold",
    // });
    return {
      message,
      // state,
    };
  },
};
</script>
