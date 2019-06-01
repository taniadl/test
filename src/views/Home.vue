<template>
  <div id="app">
    <div class="grid">
      <AddTodo class="add-todo " v-on:add-todo='addTodo'/>
      <Todos class="todos" v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
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
  }
.grid {
  display: grid;
  grid-template-rows: 20% 20% 20% 20% 20%;
}

.add-todo {
  grid-row-start: 1;
  grid-row-end: 2;
  padding: 40px;
}

.todos {
  grid-row-start: 4;
  grid-row-end: 5;

}

</style>
