<template>
  <todo-component @add="addTodo($event)" @remove="removeAll($event)">
    <list-todo :todos="todos" @remove="removeTodo($event)" />
  </todo-component>
</template>

<script>
import Todocomponent from "./components/Todocomponent";
import ListTodo from "./components/ListTodo.vue";

export default {
  name: "App",
  components: {
    "todo-component": Todocomponent,
    "list-todo": ListTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo({ title }) {
      this.todos.push(title);
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },

    removeTodo(i) {
      this.todos.splice(i, 1);
    },
    removeAll() {
      this.todos.length = 0;
    },
  },
};
</script>
