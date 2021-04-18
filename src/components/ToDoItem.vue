<template>
   <li class="list-group-item d-flex justify-content-between align-items-center">
     <span role="button">
       {{ todo.texto }}
     </span>
     <span role="button">
       <i class="fas fa-times" @click="deleteItem(todo.id)"></i>
     </span>
   </li>
</template>

<script>
import { inject } from 'vue';
export default {
  // using Props in parent Component(ToDoList)
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  setup () {
    // Get List of Todos from parent Component(ToDoApp)
    const todos = inject('todos');
    // item selected per id
    const deleteItem = (id) => {
      // will filter all items that are different from the selected id into the new list.
      todos.value = todos.value.filter(item => item.id !== id)
    }

    return { deleteItem }
  }
}
</script>

<style lang="scss" scoped>

</style>