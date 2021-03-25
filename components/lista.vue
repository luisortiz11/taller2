<template>

  <a-list :grid="{ gutter: 16, xs: 1, sm: 2, md: 3, lg: 3, xl: 4, xxl: 4 }">

      <a-list-item  v-for="(item,key) in list" :key="item.id">
          <Elemento :nombre="item.nombre" :precio="item.precio" :descripcion="item.descripcion" :label1="label1" :label2="label2" :label3="label3"  @deletear="deletear(key)" @showModal="showModal(key)"/>

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
</template>

<script>
import Productos from '/components/Prod'

export default {

  name: "Lista",
  props: {
    list: {type: Array},
    label1: { type: String },
    label2: { type: String },
    label3: {type: String },
    ph1: { type: String },
    ph2: { type: String },
    ph3: {type: String },
    nombrea: { type: String },
    precioa: { type: String },
    descripciona: {type: String },

  },
  components: {
    Productos
  },
  data: () => ({nombrea: "", precioa: "", descripciona: "", selectedItem: undefined, visible: false}),

  methods: {

    deletear(id) {
      this.$emit('deletear', id);
    },
    showModal(id) {
      this.selectedItem = id;
      this.visible = true;
      this.$emit('showModal', this.selectedItem);

    },
    handleOk(selectedItem) {
    this.$emit('handleOk', selectedItem , this.nombrea, this.precioa, this.descripciona);
    this.visible = false;

    },

  },
};

</script>
