<template>

  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
      <input type="checkbox" v-on:change="markComplete">
      {{todo.title}}
    <button @click="$emit('del-todo', todo.id)" class='del'>x</button>
    </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  methods: {
    markComplete() {
      this.todo.completed  = !this.todo.completed

    }
  }

}
</script>


<style scoped>


.is-complete {
  text-decoration: line-through;
}

.todo-item{
  text-align: left;
  background-color: #685C5C;

}

.del {
  margin-left: 600px;
}
</style>
