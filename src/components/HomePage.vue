<template>
  <div class="homepage">
    <div class="filter">
   <SelectField @update:value="pais = $event"/>
   <SendButton @buscar="pesquisarUniversidade();"/>
    </div>
   <DataTable v-if="listaUniversidade.length > 0" :lista="listaUniversidade"/>
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
.homepage{
  justify-content: space-around;
  display: flex;
  flex-direction: column;
}
.filter{
  width: 50%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
</style>
