<template>
  <div>

    <a-form :form = "form">

      <div class="form-group">
        <label for="nombre">Cargo</label>
        <a-input
          type="text"
          placeholder="Ej: Electricista"
          v-model="cargo"
          class="form-control"/>
      </div>

      <div class="form-group">
        <label for="salario">Salario</label>
        <a-input
          type="real"
          placeholder="Ej: 800"
          v-model="salario"
          class="form-control"/>
      </div>

      <div class="form-group">
        <label for="empresa">Empresa</label>
        <a-input
          type="text"
          placeholder="Ej: Marca Inc."
          v-model="Empresa"
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
                     <label for="cargoa">Cargo</label>
                     <a-input
                       type="text"
                       :placeholder="entry.cargo"
                       v-model="cargoa"
                       class="form-control"/>
                   </div>

                   <div class="form-group">
                     <label for="salarioa">Salario</label>
                     <a-input
                       type="real"
                       :placeholder="entry.salario"
                       v-model="salarioa"
                       class="form-control"/>
                   </div>

                   <div class="form-group">
                     <label for="empresaa">Empresa</label>
                     <a-input
                       type="text"
                       :placeholder="entry.empresa"
                       v-model="empresaa"
                       class="form-control"/>
                   </div>

                 </a-form>

                </a-modal>

               <p>Cargo : {{entry.cargo}}</p>
               <p>Empresa : {{entry.empresa}}</p>
               <p>Salario : {{entry.salario}}</p>

             </a-card>
        </a-list-item>

      </a-list>

  </div>



</template>


<script>

  export default {

    name: "Vacantes",
    data: () => ({ cargo: "", salario: "", empresa: "", visible: false, allelements: []}),

    computed: {
      List: function() {
        return this.allelements;

      },
    },
    methods: {

      onSubmit() {
        this.allelements.push({ cargo: this.cargo, salario: this.salario, empresa: this.empresa });
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
        this.nuevo = { cargo: this.cargoa, salario: this.salarioa, empresa: this.empresaa};
        this.allelements.push(this.nuevo);
        this.allelements.splice(j,1);
        this.cargoa = "";
        this.salarioa = "";
        this.empresaa = "";
        this.visible = false;

      },

      clearForm() {
        this.cargo = "";
        this.salario = "";
        this.empresa = "";

      },
    },
  };

</script>
