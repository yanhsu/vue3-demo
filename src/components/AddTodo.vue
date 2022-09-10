
        
        <template>
            <div class= "mb-5">
                <b-input-group class="mt-2">
                    <b-form-input   v-model="text"/>
                    <b-input-group-append> 
                    <b-button type='submit' variant= 'primary' @click="add(text)">
                        <font-awesome-icon icon="plus" />
                    </b-button>
                    </b-input-group-append>
                </b-input-group> 
            </div>
        </template>

    <script>
        export default {
            props: {
                addTodo: Function
            },
            data() {
                return {
                    text:''
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