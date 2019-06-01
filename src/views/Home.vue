<template>
  <div id="app">
    <AddTodo v-on:add-todo='addTodo'/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    <img alt="Tania's pic" src="../assets/taniaimagen.jpeg">
  </div>
</template>

<script>
import Todos from '../components/Todos';
import Header from '../components/layout/header';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [ ]
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete('https://jsonplaceholder.typicode.com/todos/${id}')
      .then(res => this.todos =this.todos.filter(todo => todo.id !== id))
      .catch(err => console.log(err));

    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,
        completed
      })

      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));

    }
  },
  created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=3')
          .then( res => this.todos = res.data)
          .catch(err => console.log(err));
  }
}
</script scoped>

  <style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }


</style>
