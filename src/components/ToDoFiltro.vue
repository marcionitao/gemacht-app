<template>
  <div class="card mt-3">
    <div class="card-body d-flex justify-content-between align-items-center">
      <span role="button" @click="filtrar('active')">Actives</span>
      <span role="button" @click="filtrar('all')">All</span>
      <span role="button" @click="filtrar('complete')">Complete</span>
    </div>
  </div>
</template>

<script>
import { inject } from 'vue';
export default {
  setup () {
    // Get List of Todos from parent Component(ToDoList)
    const estado = inject('estado');
    // function for changer the status in parent Component
    const filtrar = (valor) => {
      estado.value = valor
    }
    return { filtrar }
  }
}
</script>

<style lang="scss" scoped>

</style>