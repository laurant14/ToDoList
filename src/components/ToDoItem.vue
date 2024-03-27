<template>
    <div>
    <label>
      <input type="checkbox" v-model="completed"> 
      {{ todoItem.title }}
    </label>
    </div>
</template>


<script>

export default {
  name: 'ToDoItem',
  props: ["todoItem"],
  computed: {
    completed: {
      get() {
        return this.todoItem.completed;
      },
      
      set(value) {
        // Emit an event to notify parent component of checkbox state change
        //this will be useful when i want to go delete things from the checklist
        this.$emit('toggle-completed', value);
      }
    }
  }
}


</script>

