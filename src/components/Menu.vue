<template>
  <v-container>
    <v-row>
      <v-col>
        <v-toolbar flat color='grey lighten-4'>
          <v-toolbar-title>Warehouses</v-toolbar-title>
          <v-spacer></v-spacer>
          <nav>
            <v-btn text color="grey" to="/">Home</v-btn> 
            <v-btn text color="grey" to="/warehouses">Galpões cadastrados</v-btn> 
            <v-btn text color="grey" to="/warehouses/new">Cadastrar galpão</v-btn> 
            <v-btn text color="grey" to="/about">Sobre</v-btn>
          </nav>
        </v-toolbar>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'Menu'
  }
</script>

<style>
  nav {
    padding: 30px;
  }

  nav a {
    font-weight: bold;
    color: #2c3e50;
  }

  nav a.router-link-exact-active {
    color: #42b983;
  }
</style>