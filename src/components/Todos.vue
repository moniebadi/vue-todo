<template>
  <div>
    <div :key="todo.id" v-for="todo in todos">
      <TodoItem
        :todo="todo"
        @delTodo="(id) => $emit('delTodo', id)"
        @complete="(value) => $emit('complete', {id: todo.id, checked: value})"
        @editTodo="(obj) => $emit('editTodo', obj)"
      />
    </div>
  </div>
</template>

<script>
import TodoItem from "@/components/TodoItem.vue";

export default {
  name: "Todos",
  components: {
    TodoItem,
  },
  props: ["todos"],
};
</script>
