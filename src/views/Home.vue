<template>
  <div id="app">
    <AddTodo @add-todo="addTodo" />
    <Todos :todos="todos" @del-todo="deleteTodo" />
  </div>
</template>

<script>

import AddTodo from "../components/AddTodo";
import Todos from "../components/Todos";
import axios from "axios";

export default {
  name: 'App',
  components: {
    AddTodo,
    Todos
  },
  methods: {
    deleteTodo (id) {
      axios.post("http://localhost/vuejs/traversy_media/todolist-api/todoList/deleteItem/"+id)
      
      this.todos = this.todos.filter(todo => todo.id != id)
    },
    addTodo(todo) {
      axios.post("http://localhost/vuejs/traversy_media/todolist-api/todoList/addItem", todo)
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
    }
  },
  data (){
    return {
      todos: []
    }
  },
  created() {
    axios.get("http://localhost/vuejs/traversy_media/todolist-api/todoList/list")
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
