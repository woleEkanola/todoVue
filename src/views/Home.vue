<template>
  <div id="app">
   <CreateTodo  v-on:add-todo="addTodo" />
    <Todos v-bind:todos='todos' v-on:del-todo='deleteTodo'  v-on:complete-todo='toggleCompleteTodo'/>
    <hr>
    <Completed v-bind:todos='completed' v-on:del-todo='deleteTodo' v-on:complete-todo='toggleCompleteTodo' />
      </div>
</template>

<script>
import Todos from '../components/Todos.vue'
import Completed from '../components/Completed.vue'
import CreateTodo from '../components/CreateTodo.vue'

export default {
  name: 'Home',
  components: {
    Todos,
    Completed,
    CreateTodo
  },
   methods: {
    addTodo: function(x){
      this.todos.push(x)
    },
    deleteTodo: function(x){
      this.todos = this.todos.filter(todo =>todo.id !== x )
      this.completed = this.completed.filter(todo =>todo.id !== x )

    }
    ,
    toggleCompleteTodo: function(id){
      let x = this.todos.findIndex(xx =>{
        return xx.id == id
      })

      if(x){
      this.completed.push(this.todos[x])   // add it to completed
      this.todos = this.todos.filter(todo =>todo.id !== id )   // remove the todo from todos

      }else
      this.todos.push(this.completed[x])
      this.todos = this.todos.filter(todo =>todo.id !== x )

    }
  },
  data() {
   return { 
     todos: [
      {
        id: 1,
        title: 'Eat amala',
      },
        {
        id: 2,
        title: 'Eat Egusi',
      },
        
    ],
    completed: [
      {
        id: 3,
        title: 'Eat Efo',
      }
    ]
      }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
