<template>
  <div>
    <h2>Todos</h2>
    <div class="legend">
      <span>Double click to mark as coimplete</span>
      <span>
        <span class="incomplete-box"></span>= Incomplete
      </span>
      <span>
        <span class="complete-box"></span>= Complete
      </span>
    </div>
    <div class="todos">
      <div
        v-bind:class="{'is-complete':todo.completed}"
        @dblclick="onDblClick(todo)"
        v-for="todo in allTodos"
        v-bind:key="todo.id"
        class="todo"
      >
        {{todo.title}}
        <p class="del" @click="deleteTodo(todo.id)">
          <b>x</b>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Todos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
    onDbleClick(todo) {
      const updTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed
      };
      this.updateTodo(updTodo);
    }
  },
  computed: mapGetters(["allTodos"]),
  created() {
    this.fetchTodos();
  }
};
</script>

<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}

.todo {
  border: 1px solid white;
  background: #fbaf08;
  color: white;
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
}

.del {
  color: #ff2400;
  position: absolute;
  bottom: 3px;
  right: 20px;
  cursor: pointer;
}
.del:hover {
  color: black;
}
/* i {
  position: absolute;
  bottom: 10px;
  right: 10px;
  color: #ffffff;
  cursor: pointer;
  font-size: 100px;
} */

.legend {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}

.complete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #101357;
  border: 1px solid #fff;
}

.incomplete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #fbaf08;
  border: 1px solid #fff;
}

.is-complete {
  background: #101357;
  color: white;
}

@media (max-width: 500px) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>