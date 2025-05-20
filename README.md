# 🛠️ Data Pipeline - Grain Logistic Shipping (Medallion Architecture)

Este repositório apresenta um pipeline de dados desenvolvido no **Databricks**, estruturado com a arquitetura em camadas **Bronze**, **Silver** e **Gold**, para tratar e analisar dados logísticos da Grain Logistic.

---

## 🚀 Stack Utilizada

- Apache Spark (PySpark)
- Delta Lake
- Databricks Notebooks
- SQL
- Testes Automatizados
- Data Quality

---

## 🧱 Arquitetura Medallion

- **Bronze (Raw):** Ingestão dos dados brutos.
- **Silver (Curated):** Limpeza, normalização, padronização e qualidade.
- **Gold (Analytics):** Enriquecimento, métricas e consumo analítico.

---

## ✅ Funcionalidades Implementadas

- Leitura e ingestão de dados bruntos em CSV
- Criação de coluna de timestamp de ingestão
- Padronização de nomes de colunas (snake_case, sem acento)
- Conversão de tipos de dados
- Tratamento de valores nulos e inválidos
- Geração de métricas e novas colunas na camada Gold
- Adição de metadados
- Testes automatizados:
  - Validação de schema
  - Verificação de duplicatas
  - Checagem de valores obrigatórios
  - Integração entre camadas

---

## 📘 Notebook no Databricks

Você pode visualizar o notebook completo publicado no Databricks pelo link abaixo:

🔗 [Visualizar notebook no Databricks](https://dbc-8de1bf35-2e66.cloud.databricks.com/editor/notebooks/1382068348702030?o=3509327359834938)

🔹 Caso o link esteja indisponível, o notebook se encontra nos arquivos do projeto.

---

## 📊 Possível Integração

Este pipeline está preparado para consumo analítico por ferramentas como o **Power BI**, a partir da camada **Gold**, via conexão com Delta Lake ou exportação para outros formatos.

---

## 🗺️ Mapa de Dados

Esta seção detalha o dicionário de dados original e os campos derivados criados na camada Gold:

### Dados Originais (Bronze/Silver)

| Coluna                 | Descrição                                                                 |
|------------------------|---------------------------------------------------------------------------|
| id_envio               | Número de identificação do envio                                          |
| corredor_armazenagem   | Corredor do armazém onde o produto estava localizado                      |
| metodo_envio           | Tipo de envio: transportadora, sedex ou PAC                               |
| ligacoes_cliente       | Número de ligações do cliente sobre o envio                               |
| avaliacao_cliente      | Nota de 1 a 5 dada pelo cliente à empresa                                 |
| preco                  | Preço do produto em reais (R$)                                            |
| qtd_itens              | Quantidade de itens enviados no mesmo pacote                              |
| importancia            | Urgência do envio (baixo, médio, alto)                                    |
| genero                 | Gênero do cliente: Masculino ou Feminino                                  |
| desconto               | Desconto oferecido na compra                                              |
| peso_g                 | Peso do produto em gramas                                                 |
| entrega_no_prazo       | 1 se chegou no prazo, 0 caso contrário                                    |
| destino                | UF de destino                                                             |
| data_envio             | Data de envio do produto                                                  |
| data_entrega           | Data de entrega do produto                                                |
| avaliacao_entrega      | Nota de 0 a 5 sobre a entrega                                             |
| ingestion_timestamp    | Timestamp de ingestão dos dados                                           |

### Campos Derivados (Gold)

| Coluna                 | Descrição                                                                   |
|------------------------|-----------------------------------------------------------------------------|
| dias_entrega           | Diferença em dias entre envio e entrega                                     |
| categoria_entrega      | Classificação da entrega: expressa, normal ou lenta                         |
| avaliacao_final        | Média das avaliações do cliente e da entrega                                |
| entrega_rapida         | 1 se entregue em até 2 dias, 0 caso contrário                               |
| faixa_preco            | Classificação do preço: baixo, médio ou alto                                |
| cliente_exigente       | 1 se o cliente deu nota menor que 3 em qualquer avaliação, 0 caso contrário |

## 🧾 Dataset utilizado

- Nome: `grain_logistic_shipping.csv`
- Total de registros: 10.999
- Colunas de origem: 18
- Colunas finais (Gold): 25+

---

## 👤 Autor

LinkedIn: [linkedin.com/in/guilhermepignatari](https://linkedin.com/in/guilhermepignatari)
GitHub: [github.com/guipignatari](https://github.com/guipignatari)
