<template>
<div class="app">
  <div class="app-box">
    <Header/>
      <AddTodo v-on:add-todo="AddTodo"/>
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</div>
</template>
<script>

import Header from '../components/layout/Header'

import Todos from '../components/Todos'

import AddTodo from '../components/AddTodo'

import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Header,
    Todos,
    AddTodo
  },

  data() {
    return {
      todos: []
    }
  },
    methods: {
      deleteTodo(id) {
          this.todos = this.todos.filter(todo => todo.id !== id);
      },
      AddTodo(newTodo) {
        const { title, completed } = newTodo;

        axios.post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
       
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
      }

      },

      created() {
        axios.get('https://jsonplaceholder.typicode.com/todos?_limit=2')
        .then(res => this.todos = res.data)
        .catch(err => console.log(err))
      }
}
</script>

<style scoped>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Open Sans", sans-serif;
}

.app {
  background-color: rgb(255, 255, 255);
  display: flex;
  justify-content: center;
  margin-top: 100px;
}

.app-box {
  background:  #ffffff;
  width: 450px;
  height: 500px;
  overflow: auto;
  padding: 50px;
  box-shadow: 0 0 20px #d8d5d560;
  border-radius: 10px;
}

::-webkit-scrollbar {
    display: none;
}

</style>