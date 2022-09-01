<script setup>
import Todolist from '../components/Todolist.vue';
</script>

<template>
  <Todolist 
  :todolist="this.todolist"
  :toggleTodo="this.toggleTodo"
  :deleteTodo="this.deleteTodo"
  :addTodo="this.addTodo"
  />  
</template>

<script>
  export default {
    data() {
      return {
        todolist: [{
          title: "吃飯",
          done: false
        }]
      }
    },
    methods: {
      toggleTodo (index) {
         console.log(this.todolist[index]);
         this.todolist[index].done = !this.todolist[index].done;
         console.log(this.todolist[index].done);
      },
      deleteTodo (index) {
        this.todolist.splice(index, 1);
      },
      addTodo(title) {
        this.todolist.push(
          {
            title: title,
            done: false
          }
        )
      }
    }
  }
</script>