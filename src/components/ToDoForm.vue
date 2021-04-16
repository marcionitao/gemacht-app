<template>
  <form @submit.prevent="formulario">
    <!-- 'trim' clear space in white -->
    <input type="text" class="form-control my-3" placeholder="add Task" v-model.trim="texto">
  </form>
</template>

<script>
import { inject, ref } from 'vue'
export default {
  setup () {
    // get data from parent component e comunication
    const todos = inject('todos');
    // add text in input
    const texto = ref('');

    const formulario = () => {
      // Add Model
      if (texto.value === '') {
        console.log('vazio')
        return
      }
      const todo = {
        texto: texto.value,
        estado: false,
        id: Date.now()
      }
      // to push a new task to parent component
      todos.value.push(todo);
      // to clear
      texto.value = '';
    }

    return { formulario, texto }
  }
}
</script>

<style>

</style>