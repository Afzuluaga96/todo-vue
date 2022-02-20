<template>
  <ul class="list-group">
    <!-- TAREAS DEL TODO QUE SE VAN A DIBUJAR EN LA LISTA -->
    <todo-item
      v-for="todo in todos" :key="todo.id"
      :todo="todo"
    />

    <!-- Verificar si no existen toDos -->
    <li
      v-if="todos.length === 0"
      class="list-group-item"
    >
      No hay ToDos...
    </li>

    <!-- Mostrar el FOOTER cuando existan toDos -->
    <todo-footer
      v-if="todos.length !== 0"
    />

    <todo-filtro />
  </ul>
</template>

<script>
import { computed, inject, provide, ref } from '@vue/runtime-core'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFiltro from './TodoFiltro.vue'
export default {
  components: { TodoItem, TodoFooter, TodoFiltro },
  setup() {
    const todosTodos = inject('todos')

    // Definir el estado del filtro por defecto en 'all'
    const estado = ref('all')

    // FILTRAR 'toDo'
    const todos = computed(() => {
      if(estado.value === 'all') {
        return todosTodos.value
      }
      if(estado.value === 'active') {
        return todosTodos.value.filter(item => item.estado === false)
      }
      if(estado.value === 'complete') {
        return todosTodos.value.filter(item => item.estado === true)
      }
    })

    // Envíar estado a las otras ramas
    provide('estado', estado)

    return {
      todos
    }
  }
}
</script>
