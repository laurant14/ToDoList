<script>
import ToDoItem from "./ToDoItem";

export default {
    data(){
        return{
            terms: false
        }
    },
    name: 'ToDos',
    components: {
        ToDoItem
    },
    props: [
        "todoEntries"
    ]
}
</script>

<template>
    <div>
        <h1> My To Do List:</h1>
        <ul>
            <li v-bind:key="item.id" v-for="item in todoEntries">
                <ToDoItem v-bind:todoItem="item" />
            </li>
        </ul>
    </div>
</template>

<style scoped>

ul {
    margin-left: 100px;
    margin-right: 100px;
    margin-bottom:50px;
    text-align: left;
    list-style: none;
    border-block: blue;
    border-block-color: blue;
}

h1 {
    margin-bottom: 60px;
}
    
</style>
