<template>
   <li class="list-group-item d-flex justify-content-between align-items-center">
     <span role="button">
       {{ todo.texto }}
     </span>
     <span role="button">
       <i class="fas fa-times"></i>
     </span>
   </li>
</template>

<script>
export default {
  // using Props in parent Component(ToDoList)
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  setup () {
    

    return {}
  }
}
</script>

<style lang="scss" scoped>

</style>