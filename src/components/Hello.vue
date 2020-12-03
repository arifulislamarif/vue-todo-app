<template>
    <div class="hello">
        <h1>{{ title }}</h1>
        <p>Hello World</p>
    </div>
</template>

<script>


export default {
    name:"Hello",
    data() {
        return {
            title: "Vue Todo App"
        }
    },
}
</script>

<style scoped>
    h1{
        color:blue;
    }
</style>