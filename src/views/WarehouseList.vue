<template>
  <div>
    <h1>Galpões cadastrados</h1>

    <v-form>
      <v-container>
        <v-row class="justify-center">
          <v-col cols="12" sm="6" md="4">
            <v-text-field placeholder="Buscar galpão" v-model="term" filled rounded dense></v-text-field>
          </v-col>
        </v-row>
      </v-container>
    </v-form>

    <v-card dark>
      <v-card-text>
        <WarehouseTable :warehouses="filterWarehouse" />
      </v-card-text>
    </v-card>
    
  </div>
</template>

<script>
import Warehouse from '../components/Warehouse.vue';
import WarehouseTable from '../components/WarehouseTable.vue';

export default {
  name: 'WarehouseList',
  components:{
    Warehouse,
    WarehouseTable,
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
</style>