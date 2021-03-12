<template>
  <div>
    <h1 class="mt-4 text-center">Vacantes</h1>
    <Productos
    label1=  "Cargo"
    label2 = "Salario"
    label3 = "Empresa"
    ph1 = "Ej. Electricista"
    ph2 = "Ej. 800"
    ph3 = "Ej. Construc Inc."/>
  </div>
</template>

<script>
import Productos from '/components/Prod'

export default {
  name: 'App',
  components: {
    Productos
  }
}
</script>
