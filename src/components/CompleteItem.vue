<script>
import CompletedItem from "./CompletedItem";

export default {
    data(){
        return{
          tempCompleted: []
        }
    },
    name: 'CompleteItem',
    components: {
        CompletedItem
    },
    props: [
        "completedEntries"
    ],

    methods: {
      deleteCompleted(id) {
      // Filter out the todo item with the specified id and update the todoEntries array
      this.tempCompleted = this.completedEntries.filter(completed => completed.id !== id);
      this.$emit('updated-completed', this.tempCompleted);
    }
    }
}
</script>

<template>
  <div>
    <div>
      <h2 v-if="completedEntries.length > 0">Completed:</h2>
      <ul>
        <li v-bind:key="completed.id" v-for="completed in completedEntries">
          <CompletedItem v-bind:completedItem="completed" />
          <div class = "button-container">
          <button @click = "deleteCompleted(completed.id)"><i class="fas fa-trash-alt"></i></button>
          <button><i class="fas fa-pencil-alt"></i></button>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>



<style scoped>

ul {
  margin-bottom: 50px;
  text-align: left;
  list-style: none;
  border-block: blue;
  border-block-color: blue;
}

li {
  margin-left: 20px;
  margin-right: 60px;
  display: flex; /* Use flexbox */
  justify-content: space-between; /* Align items along the main axis with space between them */
}


button {
  display: none;
}

li:hover button {
  display: inline-block;
  width: 30px; /* Set width */
  height: 25px; /* Set height */
}

h1 {
    margin-bottom: 60px;
}

h2 {
    margin-top: 60px;
}

.button-container {
  text-align: right; /* Align buttons to the right */
}

.button-container button {
  margin-left: 5px; /* Adjust margin between buttons */
  float: right; /* Float buttons to the right */
}
    
</style>
