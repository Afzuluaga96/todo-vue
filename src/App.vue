<template>
  <div class="container">
    <!-- Comp TodoAPP -->
    <todo-app />
  </div>
</template>

<script>
import TodoApp from './components/TodoApp.vue'
import TodoForm from './components/TodoForm.vue';
export default {
  components: {TodoApp, TodoForm},
  name: "App"
};
</script>

<style>
</style>
