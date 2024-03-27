<template>
  <div id="app">
    <ToDos v-bind:todoEntries = "todoEntries"/>
    <SubmitForm @add-object="addToDoItem"/>
    <!--<button type = "submit" style="background-color: blue; color: white;">Submit</button>-->
  </div>
</template>

<script>
import ToDos from './components/ToDos'
import SubmitForm from './components/SubmitForm'
export default {
  name: 'App',
  components: {
    ToDos,
    SubmitForm
  },
  data() {
    return {
      todoEntries: [
        {
          id: 1,
          title: "Check email",
          completed: false
        },
        {
          id: 2,
          title: "Reply to Laura",
          completed: false
        },
        {
          id: 3,
          title: "Call mom",
          completed: false
        },
      ],
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
      
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  margin-left: 500px;
  margin-right:500px;

  background: #eee;
  margin-top: 60px;
  border: 2px solid black;
  padding-block: 50px;

}

/* div {
  text-align: left;
} */

</style>