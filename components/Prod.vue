<template>
  <div>
    <a-form :form = "form">

      <div class="form-group">
        <label for="nombre">Nombre</label>
        <a-input
          type="text"
          placeholder="Ej: Soda"
          v-model="nombre"
          class="form-control"/>
      </div>

      <div class="form-group">
        <label for="precio">Precio</label>
        <a-input
          type="real"
          placeholder="Ej: 1.25"
          v-model="precio"
          class="form-control"/>
      </div>

      <div class="form-group">
        <label for="descripcion">Descripción</label>
        <a-input
          type="text"
          placeholder="Ej: marca, sabor"
          v-model="descripcion"
          class="form-control"/>
      </div>

      <button type="button" @click="onSubmit" class="btn btn-dark">
        Crear
      </button>

    </a-form>


    <a-divider/>


    <a-list :grid="{ gutter: 16, xs: 1, sm: 2, md: 3, lg: 3, xl: 4, xxl: 4 }">

        <a-list-item v-for="(entry, j) in List" :key="j">
            <a-card hoverable style="width: 300px">
               <img slot="cover" alt="example" src="https://gw.alipayobjects.com/zos/rmsportal/JiqGstEfoWAOHiTxclqi.png"/>

               <template slot="actions" class="ant-card-actions">
                 <a-icon key="edit" type="edit" @click="showModal(j)"/>
                 <a-icon key="delete" type="delete" @click="deletear(j)" />
               </template>

               <a-modal v-model="visible" title="Editar"  @ok="handleOk(j)" >

                 <a-form :form = "form">

                   <div class="form-group">
                     <label for="nombrea">Nombre</label>
                     <a-input
                       type="text"
                       :placeholder="entry.nombre"
                       v-model="nombrea"
                       class="form-control"/>
                   </div>

                   <div class="form-group">
                     <label for="precioa">Precio</label>
                     <a-input
                       type="real"
                       :placeholder="entry.precio"
                       v-model="precioa"
                       class="form-control"/>
                   </div>

                   <div class="form-group">
                     <label for="descripciona">Descripción</label>
                     <a-input
                       type="text"
                       :placeholder="entry.descripcion"
                       v-model="descripciona"
                       class="form-control"/>
                   </div>

                 </a-form>

                </a-modal>

               <p>Nombre : {{entry.nombre}}</p>
               <p>Descripción : {{entry.descripcion}}</p>
               <p>Precio : {{entry.precio}}</p>

             </a-card>
        </a-list-item>

      </a-list>

  </div>



</template>


<script>

  export default {

    name: "Productos",
    data: () => ({ nombre: "", precio: "", descripcion: "", visible: false, allelements: []}),

    computed: {
      List: function() {
        return this.allelements;

      },
    },
    methods: {

      onSubmit() {

        this.allelements.push({ nombre: this.nombre, precio: this.precio, descripcion: this.descripcion });
        this.clearForm();
        this.$notification.open({
         message: 'Item creado!',
         description:
           'Puede editar o eliminar su item.'});


      },
      deletear(j) {
        this.allelements.splice(j,1);
      },
      showModal() {
        this.visible = true;

      },
      handleOk(j) {
        this.nuevo = { nombre: this.nombrea, precio: this.precioa, descripcion: this.descripciona};
        this.allelements.push(this.nuevo);
        this.allelements.splice(j,1);
        this.nombrea = "";
        this.precioa = "";
        this.descripciona = "";
        this.visible = false;

      },

      clearForm() {
        this.nombre = "";
        this.precio = "";
        this.descripcion = "";

      },
    },
  };

</script>
