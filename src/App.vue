<template>
  <div id="app">
    <Todos :todos="todos" @del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";

export default {
  name: 'App',
  components: {
    Todos
  },
  methods: {
    deleteTodo (id) {
      // console.log(id);
      this.todos = this.todos.filter(todo => todo.id != id)
    }
  },
  data (){
    return {
      todos: [
        {
          id: 1,
          title: "ToDo One",
          completed: false
        },
        {
          id: 2,
          title: "ToDo Two",
          completed: true
        },
        {
          id: 3,
          title: "ToDo Three",
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
