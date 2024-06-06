<template>
  <div>
    <h1>Galpões cadastrados</h1>

    <input class="search-form" type="text" placeholder="Buscar galpão" v-model="term">

    <div v-for="w in filterWarehouse" :key="w.id">
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
      warehouses:[],
      term: ""
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
  },

  computed:{
    filterWarehouse(){
      return this.warehouses.filter(warehouse => {
        return warehouse.name.toLowerCase().includes(this.term.toLowerCase());
      })
    }
  }
}
</script>

<style>
  .search-form {
    margin-bottom: 20px;
    font-size: 1rem;
    padding: 5px;
    border-radius: 7px;
  }
</style>