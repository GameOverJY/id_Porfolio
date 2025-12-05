# 🏁 Aula 10: Revisão Geral e Integração em Contextos Avançados

**Data:** 11/11/2025  
**Instituição:** ISEC - Instituto Superior de Engenharia de Coimbra  
**Curso:** CTeSP em Tecnologias e Programação de Sistemas de Informação  
**Professor:** João Leal  

---

## 📝 Sumário da Aula

Nesta última aula de conteúdos curriculares, realizámos uma revisão transversal dos conceitos abordados ao longo da Unidade Curricular, consolidando os fundamentos de ETL. A sessão avançou para tópicos de **Integração em Contextos Avançados**, focando-se nos desafios do Big Data, tempo real e qualidade de dados.

A aula culminou com a resolução da **Tarefa #07**, onde aplicámos processos de extração de dados via **REST APIs** e lançámos o Trabalho Final da disciplina.

* **Revisão de Fundamentos:** O ciclo de vida ETL e a heterogeneidade das fontes de dados.
* **Integração em Tempo Real:**
    * Diferença entre processamento *Batch* (Lotes) vs. *Real-Time* (Streaming).
    * Técnicas de **CDC** (Change Data Capture) para sincronização imediata.
    * Uso de *Message Queues* (ex: Apache Kafka, RabbitMQ).
* **Big Data e Arquiteturas Modernas:**
    * Os 3 Vs do Big Data: Volume, Velocidade e Variedade.
    * Evolução do armazenamento: *Data Warehouse* vs. *Data Lake* vs. *Lakehouse*.
* **Governança e Qualidade:**
    * **Data Profiling:** Análise estatística para entender a estrutura dos dados.
    * **Data Cleansing:** Processos de limpeza e normalização.
    * **MDM (Master Data Management):** Criação de uma "fonte de verdade única" para entidades críticas (Clientes, Produtos).

---

## 🛠️ Cenários Práticos: Consumo de APIs

A vertente prática focou-se na integração de sistemas distribuídos, abandonando os ficheiros locais em favor de dados dinâmicos obtidos via Web Services.

### Desafios da Tarefa #07
1.  **Consumo de APIs REST:** Utilização da biblioteca `requests` para métodos GET.
2.  **JSON Parsing:** Tratamento de dados semi-estruturados e conversão para tabelas (DataFrames).
3.  **Visualização:** Geração de gráficos a partir de dados da NASA.
4.  **Carga em Base de Dados:** Persistência dos dados transformados em SQLite.

---

## 💻 Exemplo de Implementação (ETL com API e SQLite)

Abaixo apresento a resolução do **Exercício 4**, que ilustra um pipeline completo: extrair produtos de uma API fictícia, aplicar regras de negócio (cálculo de IVA e filtragem) e carregar para uma base de dados relacional.

```python
import pandas as pd
import requests
import sqlite3

# --- 1. EXTRAÇÃO (Extract) ---
# Obter dados de produtos de uma API pública
url = "[https://fakestoreapi.com/products](https://fakestoreapi.com/products)"
response = requests.get(url)

if response.status_code == 200:
    data = response.json()
    df_produtos = pd.DataFrame(data)
    
    # --- 2. TRANSFORMAÇÃO (Transform) ---
    
    # A. Seleção de colunas relevantes
    cols = ['id', 'title', 'price', 'category']
    df_produtos = df_produtos[cols]
    
    # B. Limpeza: Remover produtos com preço 0 ou negativo
    df_produtos = df_produtos[df_produtos['price'] > 0]
    
    # C. Enriquecimento: Calcular preço com IVA (23%)
    # Regra: Novo Preço = Preço * 1.23
    df_produtos['preco_com_iva'] = df_produtos['price'] * 1.23
    df_produtos['preco_com_iva'] = df_produtos['preco_com_iva'].round(2)
    
    print(f"Dados transformados: {len(df_produtos)} registos.")
    
    # --- 3. CARGA (Load) ---
    
    # Conectar a uma base de dados SQLite local
    conn = sqlite3.connect('loja_integracao.db')
    
    # Escrever o DataFrame na tabela 'produtos'
    # if_exists='replace' recria a tabela a cada execução
    df_produtos.to_sql('produtos', conn, if_exists='replace', index=False)
    
    conn.close()
    print("Sucesso: Dados carregados na base de dados SQLite.")

else:
    print(f"Erro ao aceder à API: {response.status_code}")


