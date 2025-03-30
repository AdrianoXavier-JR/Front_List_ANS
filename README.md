# Tabela Dinâmica de Dados da API

Este projeto Vue.js exibe dados relevantes de uma API em uma tabela dinâmica. Ele busca dados de uma API local (`http://127.0.0.1:5000/top_values`) e os apresenta em um formato tabular.

## Funcionalidades

-   **Exibição de Dados Tabulares:** Apresenta os dados da API em uma tabela HTML formatada.
-   **Carregamento Assíncrono:** Utiliza `axios` para buscar os dados da API de forma assíncrona.
-   **Indicador de Carregamento:** Exibe um spinner de carregamento enquanto os dados estão sendo buscados.
-   **Estilização:** Aplica estilos CSS para melhorar a apresentação da tabela e do spinner.
-   **Dados Relevantes:** Exibe as colunas: Conta, Data, Descrição, Registro ANS, Saldo Final, e Saldo Inicial.

## Tecnologias Utilizadas

-   **Vue.js:** Framework JavaScript para construção de interfaces de usuário.
-   **axios:** Biblioteca JavaScript para fazer requisições HTTP.
-   **CSS:** Para estilização da tabela e do spinner.

## Pré-requisitos

-   Node.js e npm (Node Package Manager) instalados.
-   Uma API local rodando em `http://127.0.0.1:5000/top_values` que retorna dados no formato esperado (JSON).

## Instalação

1.  Clone o repositório:

    ```
    git clone https://github.com/AdrianoXavier-JR/Front_List_ANS.git
    ```

2.  Instale as dependências:

    ```
    npm install
    ```

## Execução

1.  Inicie o servidor de desenvolvimento:

    ```
    npm run serve
    ```

2.  Abra o navegador e acesse `http://localhost:8080`

## Estrutura do Projeto

-   `src/components/TabelaDinamica.vue`: Componente Vue que lida com a busca e exibição dos dados.
-   `src/assets/TableAns.css`: Arquivo CSS para estilização da tabela e do spinner.
-   `src/App.vue`: Componente principal da aplicação.
-   `src/main.js`: Ponto de entrada da aplicação Vue.

## Configuração da API

Certifique-se de que a API local em `http://127.0.0.1:5000/top_values` esteja configurada corretamente a partir do repositório [Queries_ANS](https://github.com/AdrianoXavier-JR/Queries_ANS) e retorne um JSON no seguinte formato:

```json
{
  "top_values": [
    {
      "id": 1,
      "CD_CONTA_CONTABIL": "12345",
      "DATA": "2023-10-26",
      "DESCRICAO": "Descrição do item",
      "REG_ANS": "ANS123",
      "VL_SALDO_FINAL": 1000.00,
      "VL_SALDO_INICIAL": 500.00
    },
    {
      "id": 2,
      "CD_CONTA_CONTABIL": "67890",
      "DATA": "2023-10-27",
      "DESCRICAO": "Outra descrição",
      "REG_ANS": "ANS456",
      "VL_SALDO_FINAL": 1500.00,
      "VL_SALDO_INICIAL": 750.00
    },
    // ... mais dados
  ]
}
