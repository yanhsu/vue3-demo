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
    <b-list-group>
        <b-list-group-item v-for=" (todo, index) in todolist">
            <b-input-group class="mt-2">
                <b-input-group-prepend is-text>
                    <b-form-checkbox :modelValue="todo.done" class="mr-n2"  @click="toggleTodo(index)"/>
                </b-input-group-prepend>
                <b-form-input readonly :class="{delline: todo.done}" v-model="todo.title"></b-form-input>
                <b-input-group-append> 
                    <b-button type='submit' variant= 'primary' @click="deleteTodo(index)">
                        <font-awesome-icon icon="trash" />
                    </b-button>
                </b-input-group-append>
            </b-input-group>
            <!-- <input type="checkbox" name="" id="" @click="toggleTodo(index)">
            <span :class="{delline: todo.done}">{{ todo.title }}</span>
            <button @click="deleteTodo(index)">delete</button> -->
        </b-list-group-item>
    </b-list-group>

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