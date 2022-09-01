<script setup>
    import TodoItem from './TodoItem.vue';
        defineProps({
          todolist: {
            type: Array,
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
                <input type="text" name="" id="" v-model="text">
                <button type="submit" @click="this.add(text)">新增</button>
            </div>
        </template>

    <script>
        export default {
            data() {
                return {
                    text: ""
                }
            },
            mounted() {
                console.log(this.$props) // false
            },
            methods: {
                add(text) {
                    this.$props.addTodo(text);
                    this.text = '';
                }
            },
        }
    </script>   