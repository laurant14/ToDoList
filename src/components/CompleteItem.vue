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
          <button @click = "deleteCompleted(completed.id)">Delete</button>
          <button>Edit</button>
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
  width: 60px; /* Set width */
  height: 25px; /* Set height */
}

h1 {
    margin-bottom: 60px;
}

h2 {
    margin-top: 60px;
}
    
</style>
