

<template>
  <div>
    <div>
      <h1> My To Do List:</h1>
      <ul>
        <!--<ToDoItem @checkbox-changed = "handleToggleCompleted"/>-->
        <li v-bind:key="item.id" v-for="item in todoEntries">
          <ToDoItem v-bind:todoItem="item" />
          <!--<ToDoItem @add-to-completed="updateCompleted"/>-->
          <button @click = "deleteToDo(item.id)">delete</button>
          <button>edit</button>
          <!--<ToDoItem @toggle-completed="handleToggleCompleted"></ToDoItem>-->
        </li>
      </ul>
    </div>
    <p1>tempcompleted:{{this.tempCompleted}}</p1>
  </div>
</template>

<script>
import ToDoItem from "./ToDoItem";
//import CompletedItem from "./CompletedItem";

export default {
    data(){
        return{
          complete: false,
          tempToDos: [],
          tempCompleted: []//need to push new todo to completed and alter 'completed' variable to be true
          //or maybe completed filters through todo to find which ones are true and populated completed based on that
        }
    },
    name: 'ToDos',
    components: {
        ToDoItem
        //CompletedItem
    },
    props: [
        "todoEntries", "completedEntries"
    ],

  methods: {
    deleteToDo(id) {
      // Filter out the todo item with the specified id and update the todoEntries array
      this.tempToDos = this.todoEntries.filter(item => item.id !== id);
      this.$emit('updated-todos', this.tempToDos);
    }
  },
    addToCompleted(newCompleted){
      this.tempCompleted = [this.completedEntries, newCompleted];
    }
}
</script>



<style scoped>

ul {
    margin-bottom:50px;
    text-align: left;
    list-style: none;
    border-block: blue;
    border-block-color: blue;
}

li {

    margin-left: 60px;
    margin-right: 60px;
}

h1 {
    margin-bottom: 60px;
}
    
</style>
