<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodos"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>

import Header from './components/Layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/Layout/AddTodo';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
  }, 
    data() {
      return {
        todos: []
      }
    },

    methods: {
      deleteTodo(id) {
        axios.delete(`https://jsonplaceholder.typicode.com/users/1/todos/${id}`)
        .then(this.todos = this.todos.filter(todo => todo.id != id))
        .catch(err => console.log(err));
        
      }, 
      addTodos(newTodo) {
        const {title, completed} = newTodo;
        axios.post('https://jsonplaceholder.typicode.com/users/1/todos', {
          title, 
          completed
        })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
      }
    },
    created() {
      axios.get('https://jsonplaceholder.typicode.com/users/1/todos?_limit=5')
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
    font-family: Arial, Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
