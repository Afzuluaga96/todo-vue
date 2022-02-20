<template>
  <form @submit.prevent="formulario">

    <!-- Input donde se va a ingresar el dato -->
      <!-- v-model.trim="texto" recibe como parametro texto que es el que tiene todas las tareas en una lista, el metodo .trim elimina los espacios del inicio y el final-->
    <input
      type="text"
      class="form-control my-3"
      placeholder="Ingrese tarea"
      v-model.trim="texto"
    >
  </form>
</template>

<script>
// Importar inject para poder inyectar la referencia de la key: 'todos' (Solo lo van a heredar los componentes hijos del que contiene la definición)
import { inject, ref } from '@vue/runtime-core'

export default {
  setup() {
    // Importa la referencia con la key: 'todos'
    const todos = inject('todos')
    // Esta referencia se coloca aquí por que es para si mismo pero puede ser accedido por los componentes hijos del formulario (si tiene)
    const texto = ref('')

    // Va a realizar una acción al ser llamado por el formulario
    const formulario = () => {
      // debug console.log(texto.value)
      if(texto.value === '') {
        console.log('está vacío')
        // Con el return vacío se inpide que se ejecute el código
        return
      }
      // todo se refiere a una sola tarea
      const todo = {
        texto: texto.value,
        estado: false,
        id: Date.now() //Date.now retorna la fecha para dar un id único (en teoria)
      }

      todos.value.push(todo)
      // debug console.log(todos.value)

      texto.value = ''
      // debug console.log(todo)
    }

    // debug
    //console.log(todos.value)
    return {
      // Retornar el formulario para que el componente pueda acceder a esta función
      texto,
      formulario
    }
  }
}
</script>

<style>

</style>
