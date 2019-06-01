<template>
  <div class="container">
    <div class="grid">
      <h1 class="todo-header">List of todos</h1>
      <div class="list-of-todos">
        <div v-bind:key="todo.id" v-for= "todo in todos">
         <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"]
}
</script>

<style scoped>

.grid {
  display: grid;
  height: 50%;
  grid-template-columns: 10% 20% 20% 20% 20% 10% ;
  grid-template-rows: 20% 20% 20% 20% 20%;
}

.todo-header {
  grid-column-start: 2;
  grid-column-end: 4;
  grid-row-start: 1 ;
  grid-row-end: 1
}

.list-of-todos {
  grid-column-start: 2;
  grid-column-end: 6;
  grid-row-start: 2;
  grid-row-end: 5;
}

</style>
