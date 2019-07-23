<template>
    <div id="app">
        <Header/>
        <AddTodo/>
        <Todos v-bind:todosArray="todosArrayData" v-on:del-todo="deleteTodo"/>
    </div>
</template>

<script>
    import Todos from './components/Todos';
    import Header from './components/layout/Header';
    import AddTodo from './components/AddTodo';

    export default {
        name: 'app',
        components: {Todos, Header, AddTodo},
        data() {
            return {
                todosArrayData: [
                    {
                        id: 1,
                        title: "Todo One",
                        completed: false
                    },
                    {
                        id: 2,
                        title: "Todo Two",
                        completed: true
                    },
                    {
                        id: 3,
                        title: "Todo Three",
                        completed: false
                    }
                ]
            }
        },
        methods: {
            deleteTodo(id) {
                this.todosArrayData = this.todosArrayData.filter(todo => todo.id !== id);
            }
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        font-family: Arial, Helvetica, sans-serif;
        line-height: 1.4;
    }
</style>
