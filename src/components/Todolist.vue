    
    <script setup>
import TodoItem from './TodoItem.vue';
import AddTodo from './AddTodo.vue';
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
      },
      addTodo: {
        type: Function,
        required: true
      }
    });
    
    </script>
    
    <template>
        <div class="greetings">
            <h1 class="green">{{ name }}</h1>
            <AddTodo
                :addTodo = "addTodo"
            />
            <TodoItem 
                :todolist = "todolist" 
                :toggleTodo = "toggleTodo"
                :deleteTodo = "deleteTodo"
            />      
        </div>
    </template>

    <script>
    export default {
        data() {
            return {
                name: "TODOLIST",
            }
        },
        mounted() {
            console.log(this.$props.todolist) // false
        }
    }
    </script>