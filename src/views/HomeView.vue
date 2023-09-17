<template>
  <div>
    <Header :title="title" />
    <AddTodo @addTodo="addTodo" />
    <Todos
      :todos="todos"
      @delTodo="deleteTodo"
      @editTodo="updateTodo"
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
      title: "",
    };
  },

  computed: {
    // todoLength() {
    //   return this.todos.length;
    // },

    lastTitle() {
      return this.todos[this.todos.length - 1].title;
    },
  },

  watch: {
    todos() {
      this.title = `Todo items: ${this.todos.length} - Last todo: ${this.lastTitle}`;
    },
  },
  methods: {
    deleteTodo(id) {
      // this.todos = this.todos.filter((todo) => todo.id !== id);
      const index = this.todos.findIndex((todo) => todo.id == id);
      this.todos.splice(index, 1);
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
      let index = this.todos.findIndex((i) => item.id == i.id);
      this.todos.splice(index, 1, item);
    },
    setComplete(item) {
      const index = this.todos.findIndex((todo) => todo.id === item.id);
      this.todos[index].completed = item.checked;
    },
  },
};
</script>
