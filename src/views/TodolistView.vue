<script setup>
import Todolist from '../components/Todolist.vue';
import { parse } from '@vue/compiler-dom';
</script>

<template>
  <Todolist 
  :todolist="todolist"
  :toggleTodo="toggleTodo"
  :deleteTodo="deleteTodo"
  :addTodo="addTodo"
  />  
</template>

<script>
  export default {
    data() {
      return {
        todolist: []
      }
    },
    mounted() {
        this.todolist = JSON.parse(localStorage.getItem('todolist')) || [];
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