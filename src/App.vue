<template>
    <div id="app">
        <Todos v-bind:todosArray="todosArrayData"/>
    </div>
</template>

<script>
    import Todos from './components/Todos';

    export default {
        name: 'app',
        components: {Todos: Todos},
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
