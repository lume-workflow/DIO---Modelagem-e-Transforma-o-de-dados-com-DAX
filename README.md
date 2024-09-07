# Projeto: Modelo Star Schema no Power BI

## Descrição do Projeto

Este projeto tem como objetivo construir um modelo de dados baseado em Star Schema a partir da tabela única `Financial Sample`. A partir dessa tabela original, foram criadas tabelas de dimensões e fatos, reorganizando os dados para melhor eficiência e clareza nas análises. O processo envolveu a criação de novas tabelas, o uso de funções DAX para agregar dados, e a construção de relações entre as tabelas para formar o esquema estrela.

## Estrutura do Projeto

### Tabelas Criadas

1. **`Financials_origem`** (modo oculto)
   - Backup da tabela original para referência futura.

2. **`D_Produtos`** (Dimensão)
   - **Colunas**: `ID_produto`, `Produto`, `Média de Unidades Vendidas`, `Média do Valor de Vendas`, `Mediana do Valor de Vendas`, `Valor Máximo de Venda`, `Valor Mínimo de Venda`.
   - **Descrição**: Esta tabela contém informações agregadas sobre os produtos, calculadas a partir da tabela `Financials_origem`.

3. **`D_Produtos_Detalhes`** (Dimensão)
   - **Colunas**: `ID_produtos`, `Discount Band`, `Sale Price`, `Units Sold`, `Manufactoring Price`.
   - **Descrição**: Tabela que detalha informações específicas dos produtos, como faixas de desconto e preços.

4. **`D_Descontos`** (Dimensão)
   - **Colunas**: `ID_produto`, `Discount`, `Discount Band`.
   - **Descrição**: Informações sobre descontos aplicados aos produtos.

5. **`D_Detalhes`** (Dimensão)
   - **Descrição**: Esta tabela agrupa informações que não foram contempladas nas outras tabelas de dimensão, fornecendo detalhes adicionais sobre as vendas.

6. **`D_Calendário`** (Dimensão)
   - **Descrição**: Tabela de calendário criada com a função DAX `CALENDAR()` para gerenciar as datas do projeto.

7. **`F_Vendas`** (Tabela Fato)
   - **Colunas**: `SK_ID`, `ID_Produto`, `Produto`, `Units Sold`, `Sales Price`, `Discount Band`, `Segment`, `Country`, `Sellers`, `Profit`, `Date`.
   - **Descrição**: Tabela principal que armazena os dados de vendas, integrando informações das tabelas de dimensões para análises detalhadas.

### Processos e Funções Utilizados

- **Agrupamento de Informações**: Utilizei a função de agrupar ` para criar a tabela `D_Produtos`, agrupando e calculando métricas como médias, medianas e valores máximos/mínimos.
- **Criação de Índices**: Índices foram gerados para garantir a unicidade nas tabelas de dimensões, utilizando a criação de coluna condicional.
- **Tabelas de Calendário**: Criadas usando a função `CALENDAR()` para facilitar a análise temporal das vendas.

### Etapas do Projeto

1. **Importação e Preparação dos Dados**:
   - A tabela `Financial Sample` foi renomeada para `Financials_origem`, que foi ocultada para servir de backup.

2. **Criação das Tabelas de Dimensões**:
   - Tabelas de dimensões foram criadas a partir da tabela `Financials_origem`, selecionando colunas específicas e calculando métricas necessárias.

3. **Criação da Tabela de Fatos**:
   - A tabela `F_Vendas` foi construída para integrar dados das tabelas de dimensões, proporcionando uma visão completa das vendas.

4. **Construção do Modelo Star Schema**:
   - As relações entre as tabelas foram definidas para formar o Star Schema, assegurando que cada tabela de dimensão se conecte diretamente à tabela de fatos.

## Conclusão

Este projeto demonstra a criação de um modelo de dados eficiente no Power BI utilizando o Star Schema. A partir de uma única tabela original, foi possível reorganizar os dados em tabelas de dimensões e fatos, melhorando a capacidade de análise e a performance das consultas. O modelo final foi salvo e está disponível para revisão no repositório GitHub, juntamente com o arquivo `.pbix` e uma imagem do diagrama do Star Schema.
