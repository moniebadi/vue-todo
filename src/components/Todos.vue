<template>
    <div>
        <div :key="todo.id" v-for="todo in todos">
            <TodoItem :todo="todo" />
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
    props: ["todos"]
}
</script>

<style scoped>

</style>


