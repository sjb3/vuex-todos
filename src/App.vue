<template>
  <div id="app">
    <div class="container">
      <AddTodo />
      <FilterTodos />
      <Todos />
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import AddTodo from "./components/AddTodo";
import FilterTodos from "./components/FilterTodos";

export default {
  name: "app",
  components: {
    Todos,
    AddTodo,
    FilterTodos
  }
};
</script>

<style>
body {
  font-family: "Rock Salt", cursive, "Courier New", Courier, monospace;
  line-height: 1.6;
  background: #fea49f;
}

.container {
  max-width: 100%;
  margin: auto;
  overflow: auto;
  padding: 1rem 2rem;
}
</style>
