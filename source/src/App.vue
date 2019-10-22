<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos :todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
import Header from './components/layout/Header';

export default {
  name: 'app',
  components: {
    Todos,
    AddTodo,
    Header
  },
  data() {
    return {
      // Array syntax: <var name>: [{item},{item}, {item}]
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false
        },
        {
          id: 2,
          title: "Todo Two",
          completed: false
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos.push(newTodo);
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
