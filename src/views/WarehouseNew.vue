<template>
  <div>
    <h1>Cadastrar Galpão</h1>

    <div class="container">

      <v-alert v-if="msg != null" type="info">{{ msg }}</v-alert type="info">

      <v-form v-on:submit.prevent>
        <v-text-field label="Nome:"       v-model="form.name"></v-text-field>
        <v-text-field label="Código:"     v-model="form.code"></v-text-field>
        <v-text-field label="Endereço:"   v-model="form.address"></v-text-field>
        <v-text-field label="Cidade:"     v-model="form.city"></v-text-field>
        <v-text-field label="CEP:"        v-model="form.cep"></v-text-field>
        <v-text-field label="Área (m²):"        v-model="form.area"></v-text-field>
        <v-textarea label="Descrição:"  v-model="form.description"></v-textarea>
        <v-btn v-on:click="postWarehouse" color="secondary">Cadastrar</v-btn>
      </v-form>
    </div>
  </div>
</template>


<script>
  export default {
    name: 'WarehouseNew',

    data(){
      return{
        msg: null,
        form:{
          name: null,
          code: null,
          address: null,
          city: null,
          cep: null,
          description: null,
          area: null
        }
      }
    },

    methods:{
      async postWarehouse(){
        try {
          await this.$http.post('http://localhost:3000/api/v1/warehouses/', {

            name:        this.form.name,
            code:        this.form.code,
            address:     this.form.address,
            city:        this.form.city,
            cep:         this.form.cep,
            description: this.form.description,
            area:        this.form.area,
            })

            this.msg = 'Galpão cadastrado com sucesso!'

        } catch (error) {

          this.msg = 'Não foi possível cadastrar novo galpão.'
          console.log(error);
        }
      }
    }
  }
</script>


<style>
</style>