<template>
  <div>
    <h1>Galpões cadastrados</h1>
    <div v-for="w in warehouses" :key="w.id">
      <Warehouse
        :id      = "w.id"
        :name    = "w.name"
        :code    = "w.code"
        :address = "w.address"
        :city    = "w.city"
        :area    = "w.area"
      />
    </div>
  </div>
</template>

<script>
import Warehouse from "../components/Warehouse.vue";

export default {
  name: 'WarehouseList',
  components:{
    Warehouse
  },

  data(){
    return{
      warehouses:[]
    }
  },

  async mounted(){
    this.getWarehouses();
  },

  methods:{
    async getWarehouses(){
      // realizando a requisição:
      const response = await this.$http.get('http://localhost:3000/api/v1/warehouses/');
      const result = await response.json();

      console.log(result);

      // add dados de result no array warehouses
      this.warehouses = result;
      return this.warehouses;
    }
  }
}
</script>

<style></style>