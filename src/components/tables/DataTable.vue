<template>
  <v-data-table
    :headers="headers"
    :items="lista"
    :items-per-page="5"
    class="elevation-1"
  ></v-data-table>
</template>

<script>
  export default {
      props:{
          lista:Array
      },
    data () {
      return {
        headers: [
          {
            text: 'Província',
            align: 'start',
            sortable: false,
            value: "provincia",
          },
          { text: 'Pais', value: 'pais' },
          { text: 'Nome', value: 'nome' },
          { text: 'Site', value: 'site' },
          { text: 'Dominio', value: 'dominio' },
          { text: 'UF', value: 'uf' },
        ],
      }
    },
  }
</script>