<template>
  <ul class="list-group">
   <!--Component Son Item using v-for for List Items and get values with Props-->
    <to-do-item v-for="todo in todos" :key="todo.id" :todo='todo'></to-do-item>
  </ul>
</template>

<script>
import { inject } from 'vue';
import ToDoItem from './ToDoItem.vue';

export default {
	components: { ToDoItem },
  component: {
    ToDoItem
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