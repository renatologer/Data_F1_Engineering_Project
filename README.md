# 🏎️ F1 Data Engineering Project

Projeto de Engenharia de Dados utilizando PySpark, Spark SQL e Databricks com dados da Fórmula 1.

---

# 📌 Objetivo

Este projeto tem como objetivo construir um pipeline de dados utilizando arquitetura em camadas (Bronze, Silver e Gold) para processar e transformar dados históricos da Fórmula 1.

O desenvolvimento foi realizado utilizando:

- PySpark
- Spark SQL
- Databricks
- Delta Lake
- Git/GitHub

---

# 🛠️ Tecnologias Utilizadas

| Tecnologia | Finalidade |
|---|---|
| Python | Linguagem principal |
| PySpark | Processamento distribuído |
| Spark SQL | Transformações analíticas |
| Databricks | Ambiente de execução |
| Delta Lake | Armazenamento dos dados |
| Git/GitHub | Versionamento |

---

# 🏗️ Arquitetura do Projeto

O projeto foi desenvolvido utilizando arquitetura Medallion:

## Bronze Layer

Camada responsável pela ingestão dos dados brutos.

Arquivos utilizados:

- Drivers
- Races
- Results
- Constructors

## Silver Layer

Camada responsável pela limpeza e transformação dos dados.

Exemplos:

- Remoção de colunas desnecessárias
- Criação de novas colunas
- Padronização de nomes
- Tratamento de tipos de dados

## Gold Layer

Camada analítica para geração de métricas.

Exemplos:

- Ranking de pilotos
- Soma total de pontos
- Estatísticas por corrida

---

# 📂 Estrutura do Projeto

```bash
f1_data/
│
├── bronze/
├── silver/
├── gold/
│
├── notebooks/
│   └── O_Project_CORRIGIDO.ipynb
│
└── README.md
```

---

# ⚙️ Principais Processamentos

## Leitura dos Dados

```python
races_df = spark.read.format("csv") \
    .option("header", True) \
    .option("inferSchema", True) \
    .load("/Volumes/workspace/f1_proje/f1_data/The_Race.csv")
```

## Transformações com PySpark

```python
from pyspark.sql.functions import year, col

silver_races_df = bronze_races_df \
    .withColumn("Ano_corrida", year(col("date"))) \
    .drop("url")
```

## Escrita em Delta

```python
silver_races_df.write.format("delta") \
    .mode("overwrite") \
    .save("/Volumes/workspace/f1_proje/f1_data/silver/races")
```

---

# 📊 Resultados

O projeto gera tabelas analíticas contendo:

- Ranking de pilotos
- Total de pontos
- Informações das corridas
- Estatísticas históricas

---

# 🚀 Como Executar

## 1. Clone o repositório

```bash
git clone https://github.com/renatologer/Data_F1_Engineering_Project.git
```

## 2. Abra no Databricks

Importe o notebook `.ipynb` no ambiente Databricks.

## 3. Execute as células em ordem

O pipeline irá:

1. Ler os arquivos CSV
2. Criar DataFrames Bronze
3. Processar dados Silver
4. Gerar tabelas Gold

---

# 📈 Competências Demonstradas

- Engenharia de Dados
- Processamento distribuído
- ETL com PySpark
- Modelagem em camadas
- Manipulação de DataFrames
- Spark SQL
- Databricks
- Versionamento com Git

---

# 👨‍💻 Autor

Renato Loger

GitHub:

https://github.com/renatologer

