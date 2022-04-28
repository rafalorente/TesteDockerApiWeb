<template>
  <div class="hello">
    <v-row class="w-100 d-flex">
   <SelectField @update:value="pais = $event"/>
   <SendButton @buscar="pesquisarUniversidade();"/>
   <DataTable v-if="listaUniversidade.length > 0" :lista="listaUniversidade"/>
   </v-row>
  </div>
</template>

<script>
import axios from 'axios';
import SelectField from './inputs/SelectField.vue'
import SendButton from './buttons/SendButton.vue'
import DataTable from './tables/DataTable.vue'

export default {
  name: 'HomePage',
  props: {
    msg: String
  },components:{
    SelectField,
    SendButton,
    DataTable
  },
  data(){
    return{
      pais: null,
      listaUniversidade: []
    }
  },
  mounted(){
  },
  methods:{
    pesquisarUniversidade(){
      axios
        .get(`https://localhost:49153/api/Universidade/GetUniversidadePorPais?pais=${this.pais.toLowerCase()}`)
        .then(response => {
          this.listaUniversidade = response.data
        });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
