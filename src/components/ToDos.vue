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
        <h1> My ToDo List:</h1>
        <ul>
            <li v-bind:key="item.id" v-for="item in todoEntries">
                <ToDoItem v-bind:todoItem="item" />
            </li>
        </ul>
    </div>
</template>
