<template>
  <div>
    {{ todos }}
    <Header :title="title"/>
    <AddTodo @add-todo="addTodo" />
    <Todos
      :todos="todos"
      @del-todo="deleteTodo"
      @editTodo="updateTodo"
      @complete="setComplete"
    />
  </div>
</template>

<script>
import Header from "@/components/layout/Header.vue";
import Todos from "@/components/Todos";
import AddTodo from "@/components/AddTodo.vue";
import { watch } from 'vue';

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
    todocomp () {
      return this.todos.length;
      }
  },

  watch: {
    todocomp () {
      console.log("ebadi")
      this.title=""
    }
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
      let index = this.todos.findIndex(i => item.id == i.id)
      this.todos.splice(index, 1, item)
      
    },
    setComplete(item) {
      const index = this.todos.findIndex((todo) => todo.id === item.id);
      this.todos[index].completed = item.checked;
    },
  },
};
</script>
