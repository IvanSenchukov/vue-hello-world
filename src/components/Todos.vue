<template>
    <div>
        <div v-bind:key="todoEntry.id" v-for="todoEntry in todosArray">
            <TodoItem v-bind:todo="todoEntry" v-on:del-todo="$emit('del-todo', todoEntry.id)"/>
        </div>
    </div>
</template>

<script>
    import TodoItem from './TodoItem'
    export default {
        name: "Todos",
        components: {
            TodoItem
        },
        props: ["todosArray"]
    }
</script>

<style scoped>

</style>