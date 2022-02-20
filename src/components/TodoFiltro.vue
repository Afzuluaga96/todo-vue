<template>
  <div class="card mt-3">

    <!-- PIE DE TABLA -->
    <div class="card-body d-flex justify-content-between aling-items-center">

      <!-- botón ACTIVOS -->
      <span
        role="button"
        @click="filtrar('active')"
      >
        Actives
      </span>

      <!-- botón All -->
      <span
        role="button"
        @click="filtrar('all')"
      >
        All
      </span>

      <!-- botón All -->
      <span
        role="button"
        @click="filtrar('complete')"
      >
        Complete
      </span>

    </div>
  </div>

</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
  setup() {
    const estado = inject('estado')
    //console.log(estado.value)

    // Filtrar con el valor de
    const filtrar = valor => {
      estado.value = valor
    }

    return {
      filtrar
    }
  }

}
</script>

<style>

</style>