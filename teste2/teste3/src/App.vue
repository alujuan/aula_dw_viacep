<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const res = await axios.get(url);
      this.endereco = res.data;
    },
  },
};
</script>

<template>
  <main>
    <h1>Buscar CEP</h1>
    <form @submit.prevent="buscar">
      <input type="text" v-model="cep" />
      <button type="submit">Buscar</button>
    </form>
    <form class="end">
      <label for="rua">Rua</label>
      <input type="text" v-model="endereco.logradouro" />
      <label for="rua">Número</label>
      <input type="text" v-model="endereco.numero" />
      <label for="rua">Bairro</label>
      <input type="text" v-model="endereco.bairro" />
    </form>
  </main>
</template>
