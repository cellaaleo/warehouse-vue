<template>
  <div>
    <h1>Cadastrar Galpão</h1>

    <div class="container">

      <div class="msg">{{ msg }}</div>

      <form v-on:submit.prevent>
        <div class="form">
          <label for="">Nome: </label>
          <input type="text" v-model="form.name" placeholder="nome do galpão">
        </div>
        <div class="form">
          <label for="">Código: </label>
          <input type="text" v-model="form.code" placeholder="código do galpão">
        </div>
        <div class="form">
          <label for="">Endereço: </label>
          <input type="text" v-model="form.address" placeholder="endereço">
        </div>
        <div class="form">
          <label for="">Cidade: </label>
          <input type="text" v-model="form.city" placeholder="cidade">
        </div>
        <div class="form">
          <label for="">CEP: </label>
          <input type="text" v-model="form.cep" placeholder="cep">
        </div>
        <div class="form">
          <label for="">Descrição: </label>
          <textarea cols="30" rows="5" v-model="form.description"></textarea>
        </div>
        <div class="form">
          <label for="">Área m²: </label>
          <input type="number" v-model="form.area">
        </div>
        <div class="form">
          <button v-on:click="postWarehouse">Cadastrar</button>
        </div>
      </form>
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
  .msg {
    color: darkblue;
    margin-bottom: 15px;
  }

  .form {
    margin-bottom: 15px;
  }

  .form input {
    margin: 5px;
  }
</style>