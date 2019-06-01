<template>
  <div>
    <h3>Add a todo</h3>
    <form @submit="addTodo">
      <input type="text" v-model='title' name='title' placeholder='Add Todo...'>
      <input type="submit" value="submit" class='btn btn-success' >
    </form>
  </div>
</template>

<script>
  export default{
    name: "AddTodo",
    data() {
      return {
        title: ''
      }
    },
    methods: {
      addTodo(e) {
        e.preventDefault();
        const newTodo = {
          title: this.title,
          completed: false
        }
        //send to parents
        this.$emit('add-todo', newTodo);
        this.title = '';
      }
    }
  }
</script>

<style>

</style>
