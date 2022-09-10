<script setup>
import Todolist from '../components/Todolist.vue';
import { parse } from '@vue/compiler-dom';
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
    mounted() {
      if(localStorage.getItem("todolist") !== null && localStorage.getItem("todolist") !== undefined) {
        this.todolist = JSON.parse(localStorage.getItem("todolist"));
        console.log(JSON.stringify(this.todolist));
      }
    }, 
    data() {
      return {
        todolist: []
      }
    },
    methods: {
      toggleTodo (index) {
        this.todolist[index].done = !this.todolist[index].done;
        this.setLocalStorage(this.todolist);
      },
      deleteTodo (index) {
        this.todolist.splice(index, 1);
        this.setLocalStorage(this.todolist);
      },
      addTodo(title) {
        this.todolist.push(
          {
            title: title,
            done: false
          }
        );
        this.setLocalStorage(this.todolist);
      },
      setLocalStorage(obj) {
        localStorage.setItem('todolist', JSON.stringify(obj));
      }
    }
  }
</script>