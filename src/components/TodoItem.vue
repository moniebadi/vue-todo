<template>
  <div class="todo-item" :class="{ 'is-complete': todo.completed }">
    <div>
      <div v-if="isEditing">
        <input v-model="newTitle" />
        <button @click="submitNewItem">submit</button>
      </div>
      <div v-else>
        <input type="checkbox" @change="markComplete" />
        <span class="title">{{ todo.title }}</span>
      </div>
    </div>
    <div>
      <button @click="edit" class="edit">edit</button>
      <button @click="$emit('delTodo', todo.id)" class="del">x</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  data() {
    return {
      newTitle: this.todo.title,
      isEditing: false,
    };
  }, 
  methods: {
    markComplete(e) {
      this.$emit("complete", e.target.checked);
    },
    edit() {
      this.isEditing = true;
    },
    submitNewItem() {
      if (this.newTitle == "") return;
      let obj = Object.assign({}, this.todo)
      obj.title = this.newTitle
      this.$emit("editTodo", obj);
      this.isEditing = false;
    },
  },
};
</script>

<style scoped>
.todo-item {
  background: f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
  display: flex;
  justify-content: space-between;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
}
.edit {
  margin-right: 8px;
  padding: 4px 8px;
  border: none;
  background: lightblue;
  border-radius: 4px;
}
.title {
  margin-left: 8px;
}
</style>
