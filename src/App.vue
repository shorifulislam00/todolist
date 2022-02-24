<template>
  <div id="app">
    <Header />
    <AddTodo @add-todo="addTodo" />
    <Todos :todos="todos" @del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from "./components/layout/Header";
import AddTodo from "./components/AddTodo";
import Todos from "./components/Todos";

export default {
  name: 'App',
  components: {
    Header,
    AddTodo,
    Todos
  },
  methods: {
    deleteTodo (id) {
      // console.log(id);
      this.todos = this.todos.filter(todo => todo.id != id)
    },
    addTodo(todo) {
      this.todos = [...this.todos, todo];
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
