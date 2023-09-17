<template>
    <div>
        <div :key="todo.id" v-for="todo in todos">
            <TodoItem :todo="todo" @del-todo="$emit('del-todo', todo.id)" @editTodo="editTodo"/>
        </div>
    </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue'

export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"],
    methods:{
        editTodo(item){
            this.$emit("editTodo", item)
        }
    }
}
</script>

<style scoped>

</style>


