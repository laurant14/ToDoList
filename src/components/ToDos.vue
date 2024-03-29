

<template>
  <div>
    <div>
      <h1> My To Do List:</h1>
      <ul>
        <!--<ToDoItem @checkbox-changed = "handleToggleCompleted"/>-->
        <li v-bind:key="item.id" v-for="item in todoEntries">
          <ToDoItem v-bind:todoItem="item" />
          <button @click = "deleteToDo(item.id)">delete</button>
          <button>edit</button>
          <!--<ToDoItem @toggle-completed="handleToggleCompleted"></ToDoItem>-->
        </li>
      </ul>
    </div>
    
  </div>
</template>

<script>
import ToDoItem from "./ToDoItem";

export default {
    data(){
        return{
          complete: false,
          tempToDos: []
        }
    },
    name: 'ToDos',
    components: {
        ToDoItem
    },
    props: [
        "todoEntries"
    ],

  methods: {
    deleteToDo(id) {
      // Filter out the todo item with the specified id and update the todoEntries array
      this.tempToDos = this.todoEntries.filter(item => item.id !== id);
      this.$emit('updated-todos', this.tempToDos);
    }
  }
    // methods: {
    //   handleToggleCompleted(){
    //     this.complete = true;
    //   }
      
    // }
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
