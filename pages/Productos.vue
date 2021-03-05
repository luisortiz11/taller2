<template>
  <div>
    <h1 class="mt-4 text-center">Productos</h1>
    <Productos/>
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
