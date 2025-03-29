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
          console.log('Resposta da API:', response.data); // Verifique se a resposta tem a estrutura correta
          this.data = response.data; // Certifique-se de que 'top_values' existe no seu 'data'
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
  
  <style scoped>
  table {
    width: 100%;
    margin-top: 20px;
    border-collapse: collapse;
  }
  
  th, td {
    padding: 10px;
    text-align: left;
  }
  
  th {
    background-color: #f2f2f2;
  }
  
  tbody tr:nth-child(even) {
    background-color: #f9f9f9;
  }
  .title{
    margin-bottom: 10%;
  }
  .spinner {
  border: 4px solid #f3f3f3; /* Cor de fundo do spinner */
  border-top: 4px solid #3498db; /* Cor do topo do spinner */
  border-radius: 50%;
  width: 150px;
  height: 150px;
  animation: spin 2s linear infinite;
  margin: 0 auto;
}
@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
  </style>
  