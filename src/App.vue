<template>
<div class="app">
  <div class="app-box">
    <Header/>
      <AddTodo v-bind:add-todo="addTodo"/>
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</div>
</template>
<script>

import Header from './components/layout/Header'

import Todos from './components/Todos'

import AddTodo from './components/AddTodo'


export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo
  },

  data() {
    return {
      todos: [
          {
            id: 1,
            title: 'Do One',
            completed: true
          },
          {
            id: 2,
            title: 'Do Two',
            completed: false
          },
          {
            id: 3,
            title: 'Do Three',
            completed: true
          }
      ]
    }
  },
    methods: {
      deleteTodo(id) {
          this.todos = this.todos.filter(todo => todo.id !== id);
      },
      AddTodo(newTodo) {
        this.todos = [...this.todos, newTodo]
      }
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
  padding: 50px;
  box-shadow: 0 0 20px #d8d5d560;
  border-radius: 10px;
}

</style>
