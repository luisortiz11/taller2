<template>
  <div>
    <a-form :form = "form">

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


    <a-list :grid="{ gutter: 16, xs: 1, sm: 2, md: 3, lg: 3, xl: 4, xxl: 4 }">

        <a-list-item  v-for="(entry,index) in List" :key="index">
            <a-card hoverable style="width: 300px">
               <img slot="cover" alt="example" src="https://gw.alipayobjects.com/zos/rmsportal/JiqGstEfoWAOHiTxclqi.png"/>
               <template slot="actions" class="ant-card-actions">
                 <a-icon key="edit" type="edit" @click="showModal(index)"/>
                 <a-icon key="delete" type="delete" @click="deletear(index)" />
               </template>


                <a-descriptions :title="entry.id + entry.nombre">
               <a-descriptions-item :label="label2">
                 {{entry.precio}}
               </a-descriptions-item>
               <a-descriptions-item :label="label3">
                  {{entry.descripcion}}
               </a-descriptions-item>
             </a-descriptions>

           </a-card>
           <a-modal v-model="visible" :item="selectedItem" title="Editar"  @ok="handleOk(selectedItem)" >

             <a-form>

               <div class="form-group">
                 <label>{{label1}}</label>
                 <a-input
                   type="text"
                   :placeholder="ph1"
                   v-model="nombrea"
                   class="form-control"/>
               </div>

               <div class="form-group">
                 <label>{{label2}}</label>
                 <a-input
                   type="real"
                   :placeholder="ph2"
                   v-model="precioa"
                   class="form-control"/>
               </div>

               <div class="form-group">
                 <label>{{label3}}</label>
                 <a-input
                   type="text"
                   :placeholder="ph3"
                   v-model="descripciona"
                   class="form-control"/>
               </div>
             </a-form>

            </a-modal>
        </a-list-item>
      </a-list>
  </div>

</template>


<script>

  export default {

    name: "Productos",
    props: {
      label1: { type: String },
      label2: { type: String },
      label3: {type: String },
      ph1: { type: String },
      ph2: { type: String },
      ph3: {type: String },

    },
    data: () => ({ida: -1, id: 1, nombre: "", nombrea: "", precio: "", precioa: "", descripcion: "", descripciona: "", visible: false, selectedItem: undefined, allelements: []}),

    computed: {
      List: function() {
        return this.allelements;

      },
    },

    methods: {


      onSubmit() {
        this.allelements.push({id: this.id++, nombre: this.nombre, precio: this.precio, descripcion: this.descripcion });
        this.clearForm();
        this.$notification.open({
         message: 'Item creado!',
         description:
           'Puede editar o eliminar su item.'});

      },
      deletear(id) {
        this.allelements.splice(id,1);
      },
      showModal(id) {
        this.selectedItem = id;
        this.nombrea = this.allelements[id].nombre;
        this.precioa = this.allelements[id].precio;
        this.descripciona = this.allelements[id].descripcion ;
        this.visible = true;

      },
      handleOk(id) {
        this.allelements[id].nombre = this.nombrea;
        this.allelements[id].precio = this.precioa;
        this.allelements[id].descripcion = this.descripciona;
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
