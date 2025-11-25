# 📘 Integração de Dados - Aula 03

**Data:** 23/09/2025  
**Instituição:** ISEC - Instituto Superior de Engenharia de Coimbra  
**Curso:** CTeSP em Tecnologias e Programação de Sistemas de Informação  
**Professor:** João Leal  

---

## 📝 Sumário da Aula

Nesta aula, explorámos o ciclo de vida da integração de dados, com foco nos processos de transformação e nas ferramentas tecnológicas de suporte:

* **Definição de ETL:** Conceitos de *Extract* (Extração), *Transform* (Transformação) e *Load* (Carga).
* **Contexto:** O papel fundamental do ETL em arquiteturas de *Data Warehousing* e *Business Intelligence* (BI).
* **Paradigmas:** Comparação entre o modelo tradicional (ETL) e a abordagem moderna (ELT).
* **Detalhamento do Processo:** Análise aprofundada das fases de extração, limpeza, agregação e carregamento.
* **Ecossistema de Ferramentas:** Soluções com interface visual (GUI) vs. Soluções baseadas em código.
* **Programação:** O uso de Python como linguagem preferencial para engenharia de dados.

---

## 🔄 O Processo ETL (Extract, Transform, Load)

O ETL é o processo padrão para consolidar dados de múltiplas fontes, garantindo uma "fonte única da verdade" (*Single Source of Truth*).

### 1. Extração (Extract)
Recolha de dados de fontes heterogéneas (Bases de dados, APIs, Ficheiros planos, IoT).
* **Carga Completa (Full Load):** Extrai a totalidade dos dados. Mais simples, mas exige mais recursos.
* **Carga Incremental:** Extrai apenas os dados novos ou alterados. Mais eficiente.
* **Staging Area:** Área temporária onde os dados repousam antes de serem transformados.

### 2. Transformação (Transform)
Fase onde se acrescenta valor, convertendo dados brutos em informação útil.
* **Limpeza (Cleansing):** Tratamento de valores nulos e remoção de duplicados.
* **Padronização:** Uniformização de formatos (ex: datas, endereços).
* **Agregação e Junção:** Combinação de diferentes fontes (ex: Vendas + Clientes).
* **Enriquecimento:** Criação de novos dados a partir dos existentes.

### 3. Carga (Load)
Carregamento final no sistema de destino.
* **Data Warehouse:** Para dados estruturados e prontos para análise.
* **Data Lake:** Para grandes volumes de dados brutos (estruturados e não estruturados).

---

## ⚔️ ETL vs. ELT

Com a evolução para a *Cloud* e *Big Data*, o paradigma mudou para aproveitar o poder de processamento dos destinos modernos.

| Característica | ETL (Tradicional) | ELT (Moderno) |
| :--- | :--- | :--- |
| **Sequência** | Extrair $\to$ Transformar $\to$ Carregar | Extrair $\to$ Carregar $\to$ Transformar |
| **Local da Transformação** | Servidor ETL dedicado (antes da carga). | Dentro do Data Warehouse de destino. |
| **Ideal Para** | Dados estruturados, conformidade e segurança rigorosa. | Big Data, velocidade de ingestão e dados não estruturados. |

---

## 🛠️ Ferramentas de Integração

### Ferramentas Visuais (GUI)
Permitem desenhar fluxos de dados (pipelines) através de interfaces "arrastar e soltar":
* **Pentaho (PDI):** Solução open-source robusta e muito utilizada.
* **Talend:** Focada em performance e geração de código Java/SQL.
* **Apache NiFi:** Especialista em gestão de fluxos de dados em tempo real (*streaming*).

### ETL com Programação (Code-Based)
Oferece controlo total e flexibilidade.
* **Linguagem:** Python (padrão da indústria).
* **Bibliotecas Principais:**
    * **Pandas:** Para manipulação e análise de dados em memória.
    * **SQLAlchemy:** Para conexão e interação com bases de dados SQL.
    * **PySpark:** Para processamento distribuído de grandes volumes de dados.
