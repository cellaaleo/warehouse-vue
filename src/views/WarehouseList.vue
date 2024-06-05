<template>
  <div>
    <h1>Galpões cadastrados</h1>
  </div>
</template>

<script>
export default {
  name: 'WarehouseList',

  async mounted(){
    this.getWarehouses();
  },

  methods:{
    async getWarehouses(){
      // realizando a requisição:
      const response = await this.$http.get('http://localhost:3000/api/v1/warehouses/');

      const result = await response.json();

      console.log(result);
    }
  }
}
</script>

<style></style>