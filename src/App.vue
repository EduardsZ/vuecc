<template>
  <div id="app">
    <h1>Todos</h1>    
    <hr>
    <Router-view />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'

export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 1, title: 'Buy bread', completed: false},
        {id: 2, title: 'Buy oil', completed: false},
        {id: 3, title: 'Buy beer', completed: false}
      ]
    }
  },
  components: {
    TodoList, AddTodo
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  },
  methods: {
    removeTodo(id){
      this.todos = this.todos.filter(t => t.id != id)
    },
    addTodo(todo){
      this.todos.push(todo)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
