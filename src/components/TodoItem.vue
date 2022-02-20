<template>
  <!-- Lista elementos de la "todo" -->
  <li class="list-group-item d-flex justify-content-between aling-items-center">

    <!-- TEXTO DEL TODO -->
    <span
      role="button"
      @click="completado(todo.id)"
      :class="{'tachado': todo.estado}"
    >
      {{todo.texto}}
    </span>

    <!-- Icono X para eliminar una tarea especifica en la lista-->
    <span role="button" @click="eliminar(todo.id)">
      <!-- Icono importado de cdnjs icons -->
      <i class="fas fa-times"></i>
    </span>
  </li>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
  // Importar un prop de todo como un objeto (No hace falta retornarlo)
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  setup() {
    // Inyectar "todos" con inject()
    const todos = inject('todos')

    // Eliminar las tareas del "todo"
    const eliminar = id => {
      todos.value = todos.value.filter(item => item.id !== id)
    }

    // Completar tarea del "todo"
    const completado = id => {
      todos.value = todos.value.map(item => {
        if(item.id === id) {
          item.estado = true
        }
        return item
      })
    }

    return {
      eliminar,
      completado
    }
  }
}
</script>

<style>
.tachado {
  text-decoration: line-through;
}
</style>