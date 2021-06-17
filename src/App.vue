<template>
  <div id="app">
    <h1>My Todo</h1>

    <addTodo 
      @add-todo="addTodo"
    />

    <hr>

    <Todolist 
      v-if="todos.length"
      v-bind:todos="todos"
      @remove-todo="removeTodo"
    />
    <p v-else> No Todos!</p>

  </div>
</template>

<script>
import Todolist from '@/components/Todolist'
import addTodo from '@/components/addTodo'
export default{
    name: 'app',
    data(){
        return{
            todos:[]
        }
    },
    mounted() {
      // fetch('http://jsonplaceholder.typicode.com/todos?_limit=3')
      // .then(response=>response.json())
      // .then(json=> {this.todos = json})
    },

    methods: {
      removeTodo(id)
      {
        this.todos=this.todos.filter(t=>t.id !== id)
      },
      addTodo(todo){
        this.todos.push(todo)
      }
    },
    components:{
        Todolist, addTodo
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
