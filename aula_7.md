# 📘 Revisão Global: Fundamentos, ETL e Qualidade de Dados

**Data:** 21/10/2025  
**Instituição:** ISEC - Instituto Superior de Engenharia de Coimbra  
**Curso:** CTeSP em Tecnologias e Programação de Sistemas de Informação  
**Professor:** João Leal  

---

## 📝 Sumário da Aula

Esta aula foi dedicada à revisão e consolidação de todos os conteúdos abordados até ao momento, preparando o terreno para as próximas fases do projeto e avaliação. A revisão focou-se na interligação entre a teoria da integração e a prática da qualidade de dados:

* **Visão Holística:** Como os Fundamentos, o ETL e a Qualidade se interligam.
* **Recapitulação de Conceitos:** Tipos de dados, arquiteturas e o pipeline ETL.
* **Qualidade de Dados:** Revisão das dimensões críticas (Precisão, Completude, Consistência).
* **Laboratório Prático:** Resolução de exercícios de integração e limpeza de dados com Python.

---

## 1. Fundamentos de Integração

O ponto de partida é sempre a necessidade de criar uma **"Single Source of Truth"** (Fonte Única da Verdade).

### Tipologia de Dados
* **Estruturados:** Rígidos e tabulares (SQL, CSV).
* **Semi-estruturados:** Flexíveis mas organizados (JSON, XML).
* **Não Estruturados:** Sem forma definida (PDF, Imagens, Logs brutos).

### Arquiteturas
* **Batch:** Processamento em intervalos (Lotes). Ideal para históricos.
* **Streaming:** Processamento contínuo. Ideal para tempo real.

---

## 2. O Pipeline ETL vs. ELT

A movimentação e transformação dos dados são o motor da integração.

| Fase | Descrição | Nota Importante |
| :--- | :--- | :--- |
| **Extract** | Extração de fontes heterogéneas. | Pode ser **Total** (tudo) ou **Incremental** (apenas o novo). |
| **Transform** | Limpeza, padronização e regras de negócio. | Onde se garante a qualidade dos dados. |
| **Load** | Carregamento no destino. | *Data Warehouse* (Analítico) ou *Data Lake* (Bruto). |

> **Nota:** No paradigma moderno (**ELT**), a transformação acontece *dentro* do destino (ex: Cloud Data Warehouse) para maior performance com Big Data.

---

## 3. Gestão da Qualidade de Dados (DQM)

Não basta mover dados; é preciso garantir que são úteis ("Fitness for use").

### As Dimensões da Qualidade
1.  **Precisão:** O dado reflete a realidade?
2.  **Completude:** Existem valores nulos ou em falta?
3.  **Consistência:** O mesmo dado é igual em todos os sistemas?
4.  **Unicidade:** Existem duplicados?
5.  **Atualidade:** O dado é recente o suficiente?

### Ciclo de Vida DQM
Definição $\to$ Avaliação (Profiling) $\to$ Melhoria (Cleansing) $\to$ Monitorização.

---

## 💻 Revisão Prática: Python para Engenharia de Dados

Um exemplo consolidado que simula um processo completo de ETL com foco na qualidade, utilizando a biblioteca `pandas`.

### Cenário
Temos um ficheiro de clientes com erros (duplicados, idades negativas) e um ficheiro de vendas. O objetivo é limpar os clientes e calcular o total de vendas apenas para clientes válidos.

```python
import pandas as pd

# --- 1. EXTRAÇÃO ---
try:
    df_clientes = pd.read_csv("clientes_raw.csv")
    df_vendas = pd.read_csv("vendas_raw.csv")
    print("Dados extraídos com sucesso.")
except FileNotFoundError:
    print("Erro: Ficheiros não encontrados.")

# --- 2. TRANSFORMAÇÃO & LIMPEZA ---

# A. Unicidade: Remover duplicados baseados no email
df_clientes = df_clientes.drop_duplicates(subset=["email"])

# B. Completude: Preencher emails em falta
df_clientes["email"] = df_clientes["email"].fillna("sem_email@exemplo.com")

# C. Validade/Precisão: Corrigir idades inválidas (negativas ou > 120)
# Define como None (nulo) para não estragar médias estatísticas
df_clientes.loc[(df_clientes["idade"] < 0) | (df_clientes["idade"] > 120), "idade"] = None

# D. Integridade Referencial: Filtrar vendas
# Manter apenas vendas cujo 'id_cliente' existe na lista de clientes limpos
vendas_validas = df_vendas[df_vendas["id_cliente"].isin(df_clientes["id_cliente"])]

# --- 3. CARGA (LOAD) ---

# Exportar dados limpos para CSV (Staging ou Final)
df_clientes.to_csv("clientes_clean.csv", index=False)
vendas_validas.to_csv("vendas_clean.csv", index=False)

print(f"Processo concluído. Total de vendas válidas: {vendas_validas['valor'].sum()}€")

