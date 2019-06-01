<template>
  <div class="container">
    <div class="grid">
      <h3 class="add-todo-title">Add a todo</h3>
      <div class="form-box">
      <form @submit="addTodo">
        <input type="text" v-model='title' name='title' placeholder='Add Todo...'>
        <input type="submit" value="submit" class='btn btn-success' >
      </form>
            </div>

    </div>
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

<style scoped>

.grid {
  display: grid;
  grid-template-columns: 20% 20% 20% 20% 20% ;
  padding: 40px;
  background-color: gray;
}

.add-todo-title {
  grid-column-start: 1;
  grid-column-end: 3;
  color: white;
}

.form-box {
  grid-column-start: 3;
  grid-column-end: 5;

}
</style>
