<script setup>
    defineProps({
      todolist: {
        type: Array,
        required: true
      },
      toggleTodo: {
        type: Function,
        required: true
      },
      deleteTodo: {
        type: Function,
        required: true
      }
    });
    
</script>

<template>
    <div v-for=" (todo, index) in todolist">
        <input type="checkbox" name="" id="" @click="toggleTodo(index)">
        <span :class="{delline: todo.done}">{{ todo.title }}</span>
        <button @click="deleteTodo(index)">delete</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
            }
        },
        mounted() {
            console.log(this.$props) // false
        }
    }
</script>

<style>
    .delline {
        text-decoration: line-through;
    }
</style>