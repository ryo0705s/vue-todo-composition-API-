<template>
  <div id="app">
    <h1>TODOアプリ</h1>
    <input v-model="state.todo" />
    <button @click="add">作成</button>
    <ul>
      <li v-for="(todo, index) in state.todos" :key="index">
        {{ todo }}<button @click="remove(index)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { reactive } from "vue";
export default {
  setup() {
    const state = reactive({
      todo: "",
      todos: [],
    });
    const add = () => {
      state.todos.push(state.todo);
      state.todo = "";
    };
    const remove = (index) => {
      state.todos.splice(index, 1);
    };
    return {
      state,
      add,
      remove,
    };
  },
};
</script>
