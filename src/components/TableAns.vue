<template>
    <div>
      <h1 class="title">Dados da API com os dados relevantes</h1>
      <table v-if="!loading" border="1">
        <thead>
          <tr>
            <th>Conta</th>
            <th>Data</th>
            <th>Descrição</th>
            <th>Registro ANS</th>
            <th>Saldo Final</th>
            <th>Saldo Inicial</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in data.top_values" :key="item.id">
            <td>{{ item.CD_CONTA_CONTABIL }}</td>
            <td>{{ item.DATA }}</td>
            <td>{{ item.DESCRICAO }}</td>
            <td>{{ item.REG_ANS }}</td>
            <td>{{ item.VL_SALDO_FINAL }}</td>
            <td>{{ item.VL_SALDO_INICIAL }}</td>
          </tr>
        </tbody>
      </table>
      <div v-else><div class="spinner" ></div></div>

    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'TabelaDinamica',
    data() {
      return {
        data: [],
        loading: true, 
      };
    },
    mounted() {
      this.fetchData();
    },
    methods: {
      async fetchData() {
        try {
          const response = await axios.get('http://127.0.0.1:5000/top_values');
          this.data = response.data;
        } catch (error) {
          console.error('Erro ao buscar dados:', error);
        } finally {
          console.log('Finalizando carregamento...');
          this.loading = false;
        }
      }
    }
  };
  </script>
  <style scoped src="./TableAns.css"></style>


  