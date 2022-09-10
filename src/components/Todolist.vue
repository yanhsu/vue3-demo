    
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
        <div>
            <b-container>
            <b-card
                header="TODOLIST"
                header-text-variant="white"
                header-tag="header"
                header-bg-variant="dark"
            >
                <AddTodo
                    :addTodo = "addTodo"
                />
                <TodoItem 
                    :todolist = "todolist" 
                    :toggleTodo = "toggleTodo"
                    :deleteTodo = "deleteTodo"
                />
            </b-card>     
            </b-container >
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