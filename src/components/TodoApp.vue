<template>
  <h1>ToDos</h1>
  <!-- Comp TodoForm -->
  <todo-form />
  <todo-list />
</template>

<script>
// Importar ref para gestionar los datos del todo
import { provide, ref, watchEffect } from 'vue'
// Importar componente todoForm para acceder a sus datos
import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue';
export default {
  components: { TodoForm, TodoList },
  setup() {
    // Guardar todos para que él mismo o los componentes hijos puedan acceder a la key de todas las tareas pendientes
    const todos = ref([])
    provide('todos', todos)

    // Realizar seguimiento a todos .length y .value (Es para debug en este caso)
      // Detecta los cambios de lo que contenga dentro para ejecutar el código en 'watchEffect()'
    watchEffect(() => {
      console.log(todos.value.length)
      console.log(todos.value)
    })
  }
};
</script>

<style></style>
