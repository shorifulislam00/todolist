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
import axios from "axios";

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
      todos: []
    }
  },
  created() {
    axios.get("https://jsonplaceholder.typicode.com/todos?_limit=10")
        .then(res => this.todos = res.data)
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
