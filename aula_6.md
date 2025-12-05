# 📘 Qualidade e Consistência de Dados

**Data:** 14/10/2025  
**Instituição:** ISEC - Instituto Superior de Engenharia de Coimbra  
**Curso:** CTeSP em Tecnologias e Programação de Sistemas de Informação  
**Professor:** João Leal  

---

## 📝 Sumário da Aula

Nesta aula, abordámos um dos pilares mais críticos da Engenharia de Dados: garantir que os dados são fiáveis e utilizáveis. O foco incidiu sobre as dimensões da qualidade, os problemas mais comuns e as estratégias de gestão (DQM).

* **Conceitos:** Introdução à Qualidade e Consistência de Dados.
* **Relevância:** A importância crítica no contexto de processos ETL.
* **Consequências:** O impacto negativo de dados de má qualidade nas organizações.
* **Dimensões:** Análise detalhada (Precisão, Completude, Atualidade, etc.).
* **Problemas:** Identificação de falhas comuns (Duplicados, Nulos, Ambíguos).
* **Gestão (DQM):** Ciclo de vida da gestão de qualidade e estratégias de melhoria.
* **Prática:** Exemplos de limpeza de dados com Python/Pandas.

---

## 💎 Introdução à Qualidade e Consistência

A **Qualidade de Dados** define-se pelo grau de adequação dos dados ao seu uso pretendido ("Fitness for use"). Não é um estado binário (bom/mau), mas uma avaliação multifacetada.

A **Consistência** assegura que os dados não apresentam contradições quando armazenados em diferentes sistemas ou formatos (ex: garantir que o cliente "João Silva" tem o mesmo NIF no sistema de Vendas e no CRM).

---

## ⚙️ Importância no Processo ETL

No contexto de ETL (Extract, Transform, Load), a qualidade é fundamental para evitar o princípio "Garbage In, Garbage Out".
* **Fiabilidade Decisória:** Dados limpos geram *insights* corretos para a gestão.
* **Eficiência Operacional:** Evita o retrabalho manual de correção de erros.
* **Conformidade:** Garante o cumprimento de regulamentos (ex: RGPD).

### Impacto de Dados de Má Qualidade
A má gestão de dados pode causar danos severos às organizações:
1.  **Decisões Erradas:** Estratégias baseadas em factos incorretos.
2.  **Perda de Receita:** Oportunidades perdidas por falta de visão sobre o cliente.
3.  **Custos Aumentados:** Desperdício de recursos na correção de problemas.
4.  **Danos Reputacionais:** Perda de confiança por parte dos clientes e parceiros.

---

## 📊 As Dimensões da Qualidade de Dados

Para avaliar a qualidade, analisamos várias dimensões críticas:

1.  **Precisão (Accuracy):** Os dados refletem a realidade? (ex: o endereço morada existe mesmo).
2.  **Completude (Completeness):** Existem valores em falta? (ex: campos obrigatórios vazios).
3.  **Atualidade (Timeliness):** Os dados estão atualizados para o momento da decisão?
4.  **Consistência (Consistency):** Os dados são uniformes entre sistemas diferentes?
5.  **Unicidade (Uniqueness):** Existem registos duplicados da mesma entidade?
6.  **Validade (Validity):** Os dados respeitam o formato e regras de negócio? (ex: idade > 0).
7.  **Relevância (Relevance):** Os dados são úteis para o propósito atual?

---

## ⚠️ Problemas Comuns e Resolução

| Problema | Descrição | Exemplo |
| :--- | :--- | :--- |
| **Duplicação** | Registos repetidos da mesma entidade. | Cliente criado duas vezes com ligeira variação no nome. |
| **Dados em Falta** | Campos nulos ou vazios (*Missing Data*). | Registo sem e-mail ou data de nascimento. |
| **Imprecisão** | Erros factuais ou de recolha. | Idade registada como "-5" ou e-mail inválido. |
| **Inconsistência** | Diferentes formatos para o mesmo dado. | Datas em `DD/MM/AAAA` num sistema e `MM-DD-YY` noutro. |
| **Ambiguidade** | Dados mal interpretados ou sem metadados claros. | Uma coluna "Código" sem saber se é de Produto ou Cliente. |

---

## 🔄 Gestão da Qualidade de Dados (DQM)

A **DQM** é um processo contínuo e cíclico, não um evento único.

### Ciclo de Vida DQM
1.  **Definição:** Estabelecer regras e requisitos de negócio.
2.  **Avaliação (Data Profiling):** Analisar o estado atual dos dados.
3.  **Melhoria:** Limpeza (*Cleansing*), Padronização e Enriquecimento.
4.  **Monitorização:** Controlo contínuo para evitar degradação da qualidade.
5.  **Governança:** Definição de políticas e responsabilidades.

---

## 🐍 Aplicação Prática: Limpeza com Python

Exemplo de *script* para limpeza e validação de dados utilizando a biblioteca `pandas`, abordando problemas de duplicados, valores nulos e integridade referencial.

```python
import pandas as pd

# 1. Carregamento e Limpeza Inicial
clientes = pd.read_csv("clientes.csv")

# Remover duplicados (Unicidade)
clientes = clientes.drop_duplicates(subset=["nome", "email"])

# Tratar valores em falta (Completude)
clientes["email"] = clientes["email"].fillna("email_desconhecido")

# Corrigir dados inválidos (Validade/Precisão)
# Define como None idades negativas ou irreais
clientes.loc[(clientes["idade"] < 0) | (clientes["idade"] > 120), "idade"] = None

# Guardar ficheiro limpo
clientes.to_csv("clientes_final.csv", index=False)

# ---------------------------------------------------------

# 2. Validação de Integridade Referencial
vendas = pd.read_csv("vendas.csv")
clientes_limpos = pd.read_csv("clientes_final.csv")

# Manter apenas vendas de clientes que existem na base de dados de clientes
vendas_validas = vendas[vendas["id_cliente"].isin(clientes_limpos["id_cliente"])]

print(f"Total de vendas válidas: {vendas_validas['valor'].sum()}")

