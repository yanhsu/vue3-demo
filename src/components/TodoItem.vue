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
        </b-list-group-item>
    </b-list-group>

</template>

<script>
    export default {
        props: {
            todolist: Array,
            toggleTodo: Function,
            deleteTodo: Function
        },
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