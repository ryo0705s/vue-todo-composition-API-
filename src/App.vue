<template>
  <div id="app">
    <h1>TODOアプリ</h1>
    <input v-model="state.todo" />
    <button @click="add">作成</button>
    <ul>
      <li v-for="(todo, index) in state.todos" :key="index">
        {{ todo }}
        <button @click="remove(index)">X</button>
        <button @click="edit(index)">編集</button>
        <br /><input v-model="state.newTodo" />
        <button @click="edited">更新</button>
      </li>
    </ul>
    <!-- <div>{{ length }}</div> -->
    <div>{{ getListLength }}</div>
    <Hello />
  </div>
</template>

<script>
import { reactive, computed } from "vue";
import Hello from "@/components/HelloWorld";
export default {
  components: { Hello },
  setup() {
    const state = reactive({
      todo: "",
      todos: [],
      // getListLength: computed(() => state.todos.length),
    });
    const add = () => {
      state.todos.push(state.todo);
      state.todo = "";
    };
    const remove = (index) => {
      state.todos.splice(index, 1);
    };
    const getListLength = computed(() => state.todos.length);
    // const length = (todos) => {
    //   state.todos.length;
    // };
    const edit = (index) => {
      state.newTodo = state.todos[index];
      // index = "";
    };
    const edited = (index) => {
      state.todos.splice(index, 1, state.newTodo);
      state.newTodo = "";
      // console.log(index, "dd");
    };
    return {
      state,
      add,
      remove,
      getListLength,
      edit,
      edited,
    };
  },
};
</script>
