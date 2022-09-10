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
            <div class= "mb-5">
                <b-input-group class="mt-2">
                    <b-form-input   v-model="text"/>
                    <b-input-group-append> 
                    <b-button type='submit' variant= 'primary' @click="this.add(text)">
                        <font-awesome-icon icon="plus" />
                    </b-button>
                    </b-input-group-append>
                </b-input-group> 
                <!-- <input type="text" name="" id="" v-model="text">
                <button type="submit" @click="this.add(text)">新增</button> -->
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