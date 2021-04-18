<template>
  <div class="container">
    <!--Component Son-->
    <to-do-app></to-do-app>
  </div>
</template>

<script>

import ToDoApp from '@/components/ToDoApp.vue'

export default {
  name: 'App',
  components: {
    ToDoApp
  }
}
</script>

<style>


</style>
