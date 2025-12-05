# 📘 Tarefa Prática #06: ETL Completo com Python e Pandas

**Data:** 04/11/2025  
**Instituição:** ISEC - Instituto Superior de Engenharia de Coimbra  
**Curso:** CTeSP em Tecnologias e Programação de Sistemas de Informação  
**Professor:** João Leal  

---

## 📝 Sumário da Aula

Nesta aula prática, focámo-nos na aplicação dos princípios de **ETL (Extract, Transform, Load)** utilizando Python. O objetivo principal foi consolidar a manipulação de estruturas de dados (`DataFrames`), o tratamento de inconsistências e a exportação de resultados para formatos estruturados.

* **Ingestão de Dados Heterogéneos:** Leitura e interpretação de ficheiros **CSV** e **JSON**.
* **Limpeza de Dados (*Data Cleaning*):** Identificação e tratamento de valores em falta (`NaN`) utilizando técnicas de imputação (média).
* **Transformação e Enriquecimento:** Criação de novas colunas calculadas baseadas em regras de negócio (Cálculo de totais).
* **Agregação de Dados:** Resumo de informações financeiras agrupadas por entidade (Cliente).
* **Persistência de Dados:** Exportação dos dados transformados para novos ficheiros CSV prontos para análise.

---

## 🛠️ Cenários Resolvidos

Realizámos exercícios práticos que simulam problemas reais de integração de dados:

### 1. Manipulação de CSV e JSON
Trabalhámos a extração de dados de vendas diárias e stock de produtos, lidando com diferentes formatos de entrada.
* **Desafio:** Converter dados semi-estruturados (JSON) de stock para um formato tabular limpo CSV.

### 2. ETL Completo e Tratamento de Falhas
O exercício central envolveu uma tabela de vendas (`vendas_brutas.csv`) que continha dados em falta.
* **Problema:** A coluna `Quantidade` continha valores nulos (`NaN`) e era necessário calcular o total gasto por cliente.
* **Regra de Negócio:** Para não perder registos, os valores em falta foram substituídos pela média aritmética da coluna.

---

## 💻 Implementação do Pipeline ETL

Abaixo apresento a solução desenvolvida para o **Exercício 3**, que integra todas as fases do ciclo de vida dos dados: Extração, Limpeza, Transformação e Carga.

### Código Python (Pandas)

```python
import pandas as pd

# --- 1. EXTRAÇÃO (Extract) ---
# Carregar o dataset de vendas brutas
# Fonte: vendas_brutas.csv
df_vendas = pd.read_csv('vendas_brutas.csv')

# --- 2. TRANSFORMAÇÃO (Transform) ---

# A. Limpeza: Tratamento de valores NaN
# Regra: Substituir valores nulos na 'Quantidade' pela média da coluna
media_qtd = df_vendas['Quantidade'].mean()
df_vendas['Quantidade'].fillna(media_qtd, inplace=True)

# B. Cálculo: Criar coluna 'Valor_Total'
# Regra: Valor_Total = Valor_Unitario * Quantidade
df_vendas['Valor_Total'] = df_vendas['Valor_Unitario'] * df_vendas['Quantidade']

# C. Agregação: Total gasto por Cliente
# Regra: Agrupar por 'Cliente_ID' e somar o 'Valor_Total'
df_final = df_vendas.groupby('Cliente_ID')['Valor_Total'].sum().reset_index()

# Renomear a coluna para o formato final exigido
df_final.rename(columns={'Valor_Total': 'Total_Gasto'}, inplace=True)

# --- 3. CARGA (Load) ---
# Exportar o resultado para um novo ficheiro CSV
# Destino: total_gasto_clientes.csv
df_final.to_csv('total_gasto_clientes.csv', index=False)

print("Pipeline ETL concluído com sucesso. Ficheiro exportado.")
# Resultado esperado no CSV final:
# Cliente_ID,Total_Gasto
# 101,447.2
# 102,90.5
# 103,300.0
