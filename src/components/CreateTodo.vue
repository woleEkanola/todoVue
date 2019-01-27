<template>
<form @submit="addTodo">
        <input type="text" placeholder="Enter your todo here" v-model="newTodo" name='title'  >
        <input type="submit">

</form>
</template>

<script>
export default {
    name: 'CreateTodo', 
    methods: {
        addTodo: function(e){
 e.preventDefault();
 const x = Math.random() * 1000
      const newTodo = {
          id: this.newTodo + x,
        title: this.newTodo,
        done: false
      }
      // Send up to parent
      this.$emit('add-todo', newTodo);
      this.newTodo = '';        }

    },
    data (){
        return {
            newTodo: ''
        }
    }

}
</script>

<style>

</style>
