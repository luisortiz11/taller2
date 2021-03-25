<template>
  <div>
    <h1 class="mt-4 text-center">Productos</h1>
    <Productos
    label1=  "Nombre"
    label2 = "Precio"
    label3 = "Descripción"
    ph1 = "Ej. Soda"
    ph2 = "Ej. 1.25"
    ph3 = "Ej. Sabor Fresa"/>

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
