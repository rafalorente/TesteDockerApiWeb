<template>
  <v-container fluid>
    <v-row align="center">
      <v-col class="d-flex" cols="12" sm="6">
        <v-select v-model="itemSelecionado" :items="paises" label="Selecione um país" outlined @change="$emit('update:value', itemSelecionado)" ></v-select>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return { paises: ["Brazil", "Turkey", "UnitedStates"],itemSelecionado: null };
  },
};
</script>