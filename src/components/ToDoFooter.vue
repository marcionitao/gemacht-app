<template>
  <li class="list-group-item d-flex justify-content-between align-items-center">
     <span role="button">
       {{contarItemsActives}} Actives 
     </span>
     <span role="button" @click="deleteAllCompleted">
      delete all completed
     </span>
   </li>
</template>

<script>
import { computed, inject } from 'vue';

export default {
  setup () {
    // Get List of Todos from parent Component(ToDoApp)
    const todos = inject('todos');
    const contarItemsActives = computed(() => {
      return todos.value.filter(item => item.estado === false).length;
    })

    const deleteAllCompleted = () => {
      todos.value = todos.value.filter(item => item.estado === false);
    }
   
    return { contarItemsActives, deleteAllCompleted }
  }
}
</script>

<style lang="scss" scoped>

</style>