<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todosArray="todosArrayData" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
  import Todos from '../components/Todos';
  import Header from '../components/layout/Header';
  import AddTodo from '../components/AddTodo';

  import axios from 'axios';

  export default {
    name: 'Home',
    components: {Todos, Header, AddTodo},
    data() {
      return {
        todosArrayData: []
      }
    },
    methods: {
      deleteTodo(id) {
        axios.delete('https://jsonplaceholder.typicode.com/todos/${id}')
                .then(res => this.todosArrayData = this.todosArrayData.filter(todo => todo.id !== id))
                .catch(err => console.log(err));
      },
      addTodo(newTodo) {
        const {title, completed} = newTodo;

        axios.post('https://jsonplaceholder.typicode.com/todos', {title, completed})
                .then(res => this.todosArrayData = [...this.todosArrayData, res.data])
                .catch(err => console.log(err));

      }
    },
    created() {
      fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
              .then(res => res.json())
              .then(json => this.todosArrayData = json)
              .catch(err => console.log(err));
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
