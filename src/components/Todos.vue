<template>
    <div>
        <div v-bind:key="todoEntry.id" v-for="todoEntry in todosArray">
            <h3>{{todoEntry.title}}</h3>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Todos",
        props: ["todosArray"]
    }
</script>

<style scoped>

</style>