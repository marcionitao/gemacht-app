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
  </ul>
</template>

<script>
import { inject } from 'vue';
import ToDoItem from './ToDoItem.vue';
import ToDoFooter from './ToDoFooter.vue';

export default {
  components: {
    ToDoItem,
    ToDoFooter
  },
  setup () {
    // Get List of Todos from parent Component(ToDoApp)
    const todos = inject('todos');

    return { todos }
  }
}
</script>

<style lang="scss" scoped>

</style>