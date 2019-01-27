<template>
    <h3 v-bind:class="{'iscompleted':todo.done}"> 
         {{todo.title}}
       <input type="checkBox" v-on:change="$emit('complete-todo', todo.id)">
       <span @click="$emit('del-todo', todo.id)" >x</span>


         
         </h3>
</template>


<script>
export default {
          name: 'Todo',
  props: ["todo"],
    methods: {
    markComplete() {
      this.todo.done = !this.todo.done;
    },
  
}
}
</script>

<style scoped>
.iscompleted{
        text-decoration: line-through;

}
</style>

