<template>
    <header class="header">
        <h1>TodoList {{ title }} </h1>
    </header>
</template>

<script>
export default {
    name: "Header",
    props: {
        title: {
            type: String,
            default: ""
        }
    }
}
</script>

<style scoped>
.header {
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px;
}

.header a {
    color: #fff;
    padding-right: 5px;
}
</style>