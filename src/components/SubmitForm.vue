<template>
    <form>
        <input type="text" v-model="title">
        <button @click="addToDo">Submit</button>
    </form>
</template>


<script>
import { v4 as uuidv4 } from 'uuid';

export default {
       // name: 'AddToDoButton',
        data(){
            return {
                title: ''
            }
        },
            methods: {
                addToDo(event){
                    event.preventDefault();
                    const newTodo = 
                    { 
                        id: uuidv4() ,
                        title: this.title,
                        completed: false,
                        dueDate: '2024-04-01'
                        
                    }; 
                    this.$emit('add-object', newTodo);
                    this.title='';
                    
                }

            }
        }
    
</script>

