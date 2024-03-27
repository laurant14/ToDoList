<template>
    <form>
        <input type="text" v-model="title">
        <input type="date" v-model="dueDate">
        <button @click="addToDo">Submit</button>
    </form>
</template>


<script>
import { v4 as uuidv4 } from 'uuid';

export default {
       // name: 'AddToDoButton',
        data(){
            return {
                title: '',
                dueDate: 'N/A'
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
                        dueDate: this.dueDate
                        
                    }; 
                    this.$emit('add-object', newTodo);
                    this.title='';
                    this.dueDate='N/A';
                    
                }

            }
        }
    
</script>

