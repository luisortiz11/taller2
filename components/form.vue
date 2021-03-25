<template>
  <div>
    <a-form>

      <div class="form-group">
        <label>{{label1}}</label>
        <a-input
          type="text"
          :placeholder="ph1"
          v-model="nombre"/>
      </div>

      <div class="form-group">
        <label>{{label2}}</label>
        <a-input
          type="real"
          :placeholder="ph2"
          v-model="precio"/>
      </div>

      <div class="form-group">
        <label>{{label3}}</label>
        <a-input
          type="text"
          :placeholder="ph3"
          v-model="descripcion"/>
      </div>

      <button type="button" @click="onSubmit()" class="btn btn-dark">
        Crear
      </button>
    </a-form>

    <a-divider/>

  </div>

</template>


<script>
import Productos from '/components/Prod'

  export default {

    name: "Form",
    props: {

      label1: { type: String },
      label2: { type: String },
      label3: {type: String },
      ph1: { type: String },
      ph2: { type: String },
      ph3: {type: String },

    },
    data: () => ({id: 0, nombre: "", nombrea: "", precio: "", precioa: "", descripcion: "", descripciona: "", allelements: []}),
    components: {
      Productos
    },

    methods: {


      onSubmit() {
        this.allelements.push({id: this.id++, nombre: this.nombre, precio: this.precio, descripcion: this.descripcion});
        this.clearForm();
        this.$notification.open({
         message: 'Item creado!',
         description:
           'Puede editar o eliminar su item.'});
        this.$emit('save', this.allelements);

         },

         clearForm() {
           this.nombre = "";
           this.precio = "";
           this.descripcion = "";

      },
    },
  };

</script>
