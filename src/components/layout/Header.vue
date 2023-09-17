<template>
    <header class="header">
        <h1> {{ title }} </h1>
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
    height: 60px;
}

.header a {
    color: #fff;
    padding-right: 5px;
}
</style>