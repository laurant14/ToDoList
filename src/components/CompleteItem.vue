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
      <h2>Completed:</h2>
      <ul>
        <li v-bind:key="completed.id" v-for="completed in completedEntries">
          <CompletedItem v-bind:completedItem="completed" />
          <button @click = "deleteCompleted(completed.id)">delete</button>
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
  margin-left: 60px;
  margin-right: 60px;
  display: flex; /* Use flexbox */
  justify-content: space-between; /* Align items along the main axis with space between them */
}

button {
  /* Set buttons to display inline-block */
  display: inline-block;
  width: 50px; /* Set width */
  height: 30px; /* Set height */
}

h1 {
    margin-bottom: 60px;
}

h2 {
    margin-top: 60px;
}
    
</style>
