<template>
  <div>
    <label>
      <input type="checkbox" v-model="isChecked">
      {{ isChecked }}
      {{ todoItem.title }} 
      <pre> Due: {{ todoItem.dueDate }} </pre>
    </label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      //v-model automatically handles the change of isChecked, so we don't need an event handler
      isChecked: false,
    }
  },
  name: 'ToDoItem',
  props: [
    "todoItem"
  ],  
  watch: {
    isChecked(newVal) {
      if (newVal) {
        // If isChecked is true, add the todoItem to CompletedArray
        this.$emit('add-to-completed', this.todoItem);
      } else {
        // If isChecked is false, remove the todoItem from CompletedArray
        this.$emit('remove-from-completed', this.todoItem);
      }
    }
  }
}

</script>
