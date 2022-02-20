<template>
  <li class="list-group-item d-flex justify-content-between aling-items-center">
    <!-- TEXTO DEL TODO -->
    <span
      role="button"
    >
      {{contarActivos}} Activos
    </span>

    <!-- Icono X para eliminar una tarea especifica en la lista-->
    <span role="button" @click="eliminarCompletados">
      <!-- Icono importado de cdnjs icons -->
      Eliminar Completados
    </span>
  </li>
</template>

<script>
import { computed, inject } from '@vue/runtime-core'
export default {
  setup() {
    const todos = inject('todos')

    const contarActivos = computed(() => {
      return todos.value.filter(item => item.estado === false).length
    })

    const eliminarCompletados = () => {
      todos.value = todos.value.filter(item => item.estado === false)
    }

    return {
      contarActivos,
      eliminarCompletados
    }
  }
}
</script>

<style>

</style>