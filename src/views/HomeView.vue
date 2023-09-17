<template>
  <div>
    <Header />
    <AddTodo @add-todo="addTodo" />
    <Todos
      :todos="todos"
      @del-todo="deleteTodo"
      @edit-todo="updateTodo"
      @complete="setComplete"
    />
  </div>
</template>

<script>
import Header from "@/components/layout/Header.vue";
import Todos from "@/components/Todos";
import AddTodo from "@/components/AddTodo.vue";

export default {
  name: "HomeView",
  components: {
    Header,
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      // this.todos = this.todos.filter((todo) => todo.id !== id);
      const index = this.todos.findIndex((todo) => todo.id == id)
      this.todos.splice(index, 1)
    },
    addTodo(newTodo) {
      if (
        this.todos.find(
          (todo) => todo.title.toLowerCase() === newTodo.title.toLowerCase()
        )
      ) {
        return;
      }
      this.todos.push(newTodo);
      // this.todos = [...this.todos, newTodo];
    },
    updateTodo(item) {
      const index = this.todos.findIndex((todo) => todo.id === item.id);
      this.todos[index].title = item.title;
    },
    setComplete(item) {
      const index = this.todos.findIndex((todo) => todo.id === item.id);
      this.todos[index].completed = item.checked;
    },
  },
};
</script>
