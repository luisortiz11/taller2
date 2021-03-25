<template>
  <div>
    <Form :label1="label1" :label2="label2" :label3="label3" :ph1="ph1" :ph2="ph2" :ph3="ph3"  @save="save"/>
    <Lista :list="allelements" :label1="label1" :label2="label2" :label3="label3" :ph1="ph1" :ph2="ph2" :ph3="ph3" :nombrea="nombrea" :precioa="precioa" :descripciona="descripciona" @deletear="deletear" @showModal="showModal" @handleOk="handleOk" />
  </div>

</template>


<script>
import Form from '/components/form'
import Lista from '/components/lista'

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
    data: () => ({ visible: false, nombrea: "", precioa: "", descripciona: "", selectedItem: undefined, allelements: undefined}),

    components: {
      Form,
      Lista
    },

    methods: {
      save(allelements) {
        this.allelements = allelements;
      },
      deletear(id) {
        this.allelements.splice(id,1);
      },
      showModal(id) {
        this.nombrea = this.allelements[id].nombre;
        this.precioa = this.allelements[id].precio;
        this.descripciona = this.allelements[id].descripcion;
      },
      handleOk(id, nombrea, precioa, descripciona) {
        this.allelements[id].nombre = nombrea;
        this.allelements[id].precio = precioa;
        this.allelements[id].descripcion = descripciona;
        this.nombrea = "";
        this.precioa = "";
        this.descripciona = "";
      },
    },
  };

</script>
