<template>
  <a-card hoverable style="width: 300px">
     <img slot="cover" alt="example" src="https://gw.alipayobjects.com/zos/rmsportal/JiqGstEfoWAOHiTxclqi.png"/>
     <template slot="actions" class="ant-card-actions">
       <a-icon key="edit" type="edit" @click="showModal()"/>
       <a-icon key="delete" type="delete" @click="deletear()" />
     </template>


      <a-descriptions :title="nombre">
     <a-descriptions-item :label="label2">
       {{precio}}
     </a-descriptions-item>
     <a-descriptions-item :label="label3">
        {{descripcion}}
     </a-descriptions-item>
   </a-descriptions>

 </a-card>
</template>


<script>
import Lista from '/components/lista'

  export default {

    name: "Elemento",
    props: {
      label1: { type: String },
      label2: { type: String },
      label3: {type: String },
      nombre: { type: String },
      precio: { type: String },
      descripcion: {type: String },

    },
    data: () => ({}),
    components: {
      Lista
    },

    methods: {
      deletear() {
        this.$emit('deletear');
      },
      showModal() {
        this.$emit('showModal');
      },
    },
  };

</script>
