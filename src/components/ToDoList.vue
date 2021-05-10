<template>
  <ul class="list-group">
   <!--Component Son Item using v-for for List Items and get values with Props-->
    <to-do-item v-for="todo in todos" :key="todo.id" :todo='todo'></to-do-item>
    <!-- Message for not Items-->
    <li v-if="todos.length === 0" class="list-group-item">
      Not Items
    </li>
    <!-- Component Son Footer-->
    <to-do-footer v-if="todos.length !== 0"></to-do-footer>

     <!-- Component Son Filtro-->
     <to-do-filtro></to-do-filtro>
  </ul>
</template>

<script>
import { computed, inject, ref, provide } from 'vue';
import ToDoItem from './ToDoItem.vue';
import ToDoFooter from './ToDoFooter.vue';
import ToDoFiltro from './ToDoFiltro.vue';

export default {
  components: {
    ToDoItem,
    ToDoFooter,
    ToDoFiltro
  },
  setup () {
    // Get List of Todos from parent Component(ToDoApp)
    const todosTodos = inject('todos');
    // used to filter in Son component Filtro
    const estado = ref('all');
    const todos = computed(() => {
      if (estado.value === 'all') {
        return todosTodos.value
      }
      if (estado.value === 'active') {
        return todosTodos.value.filter(item => item.estado === false);
      }
      if (estado.value === 'complete') {
        return todosTodos.value.filter(item => item.estado === true);
      }
    })
    // here is the parent component that will be accessed by the child component
    // option for changer the status of a Son Component
    provide('estado', estado);

    return { todos }
  }
}
</script>

<style lang="scss" scoped>

</style>