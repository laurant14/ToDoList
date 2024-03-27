<template>
  <div id="app">
    <ToDos v-bind:todoEntries = "todoEntries"/>
    <SubmitForm @add-object="addToDoItem"/>
    <CompleteItem v-bind:completedEntries = "completedEntries"/>
   <!-- <ToDos :todoEntries="todoEntries" @toggle-completed="handleToggleCompleted" />-->
    
    <!--<button type = "submit" style="background-color: blue; color: white;">Submit</button>-->
  </div>
</template>

<script>
import ToDos from './components/ToDos'
import CompleteItem from './components/CompleteItem'
import SubmitForm from './components/SubmitForm'
export default {
  name: 'App',
  components: {
    ToDos,
    CompleteItem,
    SubmitForm
  },
  data() {
    return {
      todoEntries: [
        {
          id: 1,
          title: "Check email",
          completed: false,
          dueDate: '2024-04-01'
        },
        {
          id: 2,
          title: "Reply to Laura",
          completed: false,
          dueDate: '2024-04-10'
        },
        {
          id: 3,
          title: "Call mom",
          completed: false,
          dueDate: '2024-05-23'
        },
      ],
      completedEntries: [
        {
          id: 10,
          title: "write app",
          completed: true,
          dueDate: '2024-03-01'
        },
                {
          id: 11,
          title: "write book",
          completed: true,
          dueDate: '2024-03-01'
        },
      ]
    }
  },

  methods: {
    addToDoItem(newToDoItem) {
      if(newToDoItem.title !==''){
        this.todoEntries.push(newToDoItem);
      }
      else{
        console.log("empty")
      }
      
    },
    // addCompletedItem(newCompletedItem) {
    //   if(newCompletedItem.title !=='' && newCompletedItem.complete == true){
    //     this.completedEntries.push(newCompletedItem);
    //   }
    //   else{
    //     console.log("empty")
    //   }
      
    // }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}

body {
  margin-left: 500px;
  margin-right:500px;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  background: #eee;
  margin-top: 60px;
  border: 2px solid black;
  padding-block: 50px;

}

/* div {
  text-align: left;
} */

</style>