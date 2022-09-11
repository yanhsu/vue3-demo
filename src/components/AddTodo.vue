
        
        <template>
            <div class= "mb-5">
                <b-input-group class="mt-2">
                    <b-form-input
                        autofocus
                        :state="textValidate"  
                        v-model="text"
                        placeholder="Enter your todo"
                        aria-describedby="input-live-feedback"
                        :change="changeInput()"
                    />
                    <b-input-group-append> 
                    <b-button type='submit' variant= 'primary' @click="add(text)">
                        <font-awesome-icon icon="plus" />
                    </b-button>
                    </b-input-group-append>
                    <b-form-invalid-feedback id="input-live-feedback">
                        Enter at least 1 letter
                    </b-form-invalid-feedback>
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
                    text:'',
                    textValidate: false
                }
            },
            mounted() {
                console.log(this.$props) // false
            },
            methods: {
                add(text) {
                    if(text.length == 0) {
                        return;
                    }
                    this.$props.addTodo(text);
                    this.text = '';
                },
                changeInput() {
                    // console.log(this.text);
                    this.textValidate = this.text.length > 0? true : false;
                }
            },
        }
    </script>   