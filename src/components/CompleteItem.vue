<script>
import CompletedItem from "./CompletedItem";

export default {
    data(){
        return{
        }
    },
    name: 'CompleteItem',
    components: {
        CompletedItem
    },
    props: [
        "completedEntries"
    ]
}
</script>

<template>
  <div>
    <div>
      <h2>Completed:</h2>
      <ul>
        <li v-bind:key="completed.id" v-for="completed in completedEntries">
          <CompletedItem v-bind:completedItem="completed" />
        </li>
      </ul>
    </div>
  </div>
</template>



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

h2 {
    margin-top: 60px;
}
    
</style>
