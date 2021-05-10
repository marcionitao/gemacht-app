<template> 
  <h1>ToDos</h1>
  <!--Component Son Form-->
  <to-do-form></to-do-form>
  <!--Component Son List-->
  <to-do-list></to-do-list>
</template>

<script>
import { provide, ref, watchEffect } from 'vue';
import ToDoForm from './ToDoForm.vue';
import ToDoList from './ToDoList.vue';

export default {
  components: {
    ToDoForm,
    ToDoList
  },
  setup () {
    // alternative to Vuex
    // here is the parent component that will be accessed by the child component
    const todos = ref([]);
    // option for changer the status of a Son Component
    provide('todos', todos);

    // watchEffect is one of the ways to track reactive dependencies in Vue3. 
    // when the values are updated the method is run
    watchEffect(() => {
      console.log(todos.value.length);
    })

    return {}
  }
}
</script>

<style>

</style>