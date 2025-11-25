# 📘 Integração de Dados - Aula 03

**Data:** 23/09/2025
[cite_start]**Instituição:** ISEC - Instituto Superior de Engenharia de Coimbra [cite: 1]
[cite_start]**Curso:** CTeSP em Tecnologias e Programação de Sistemas de Informação [cite: 4]
[cite_start]**Professor:** João Leal [cite: 6]

---

## 📝 Sumário da Aula

Nesta aula, explorámos em profundidade o ciclo de vida dos dados e as ferramentas utilizadas para a sua manipulação:

* **Definição de ETL:** Conceitos de *Extract* (Extração), *Transform* (Transformação) e *Load* (Carga).
* **Contexto:** O papel crucial do ETL em *Data Warehousing* e *Business Intelligence*.
* **Paradigmas de Integração:** Comparação entre o modelo tradicional (ETL) e a abordagem moderna (ELT).
* **Processos Detalhados:** Análise das fases de extração, limpeza, agregação e carregamento.
* **Ferramentas:** Panorama de software GUI (Pentaho, Talend) vs. Programação (Python).
* **Prática:** Introdução ao Python como linguagem de engenharia de dados.

---

## 🔄 O Processo ETL (Extract, Transform, Load)

[cite_start]O ETL é o processo padrão para consolidar dados de múltiplas fontes, criando uma "fonte única da verdade"[cite: 28].

### 1. Extração (Extract)
[cite_start]Recolha de dados de fontes heterogéneas (BDs relacionais, APIs, ficheiros CSV/JSON, IoT)[cite: 135].
* **Carga Completa (Full Load):** Extrai todos os dados. [cite_start]Mais simples, mas mais pesado[cite: 163].
* **Carga Incremental:** Extrai apenas dados novos ou alterados. [cite_start]Mais eficiente[cite: 165].
* [cite_start]**Staging Area:** Os dados são movidos para uma área temporária antes da transformação[cite: 153].

### 2. Transformação (Transform)
[cite_start]Fase onde se acrescenta valor, convertendo dados brutos em informação consistente[cite: 210, 212].
* [cite_start]**Limpeza:** Tratamento de nulos e remoção de duplicados[cite: 224].
* [cite_start]**Padronização:** Uniformização de formatos (ex: datas, moedas)[cite: 225].
* [cite_start]**Agregação e Junção:** Combinação de fontes (ex: Vendas + Clientes) e resumos de dados[cite: 238, 239].
* [cite_start]**Enriquecimento:** Criação de novos dados calculados[cite: 256].

### 3. Carga (Load)
[cite_start]Carregamento final no sistema de destino, tipicamente um *Data Warehouse* (dados estruturados) ou *Data Lake* (dados brutos)[cite: 299, 301].

---

## ⚔️ ETL vs. ELT

Com a evolução para a *Cloud* e *Big Data*, surgiu o ELT (*Extract, Load, Transform*), invertendo as últimas fases.

| Característica | ETL (Tradicional) | ELT (Moderno) |
| :--- | :--- | :--- |
| **Sequência** | Extrair $\to$ Transformar $\to$ Carregar | [cite_start]Extrair $\to$ Carregar $\to$ Transformar [cite: 354] |
| **Transformação** | Ocorre num servidor dedicado antes da carga. | [cite_start]Ocorre dentro do destino (Data Warehouse moderno)[cite: 367]. |
| **Cenário Ideal** | [cite_start]Dados estruturados, transformações complexas, segurança de dados sensíveis[cite: 389, 391]. | [cite_start]Big Data, necessidade de velocidade de ingestão, dados não estruturados[cite: 419, 421]. |

---

## 🛠️ Ferramentas de Integração

### Ferramentas Visuais (GUI)
[cite_start]Permitem criar fluxos "arrastar e soltar" (*drag-and-drop*)[cite: 448].
* [cite_start]**Pentaho (PDI):** Open-source, robusto e flexível[cite: 459].
* [cite_start]**Talend:** Gera código Java/SQL, focado em performance[cite: 473].
* [cite_start]**Apache NiFi:** Focado em *streaming* e roteamento de dados em tempo real[cite: 488].

### ETL com Programação (Code-Based)
[cite_start]Oferece máxima flexibilidade e controlo[cite: 505]. [cite_start]A linguagem de eleição é o **Python**[cite: 515].

**Bibliotecas Essenciais:**
* [cite_start]**Pandas:** Manipulação e análise de dados (Leitura de CSV/JSON, Limpeza, Junções)[cite: 532].
* [cite_start]**SQLAlchemy:** Comunicação com bases de dados SQL[cite: 543].
* [cite_start]**PySpark:** Processamento de Big Data distribuído[cite: 546].

---

> [cite_start]💡 *"Sem um processo ETL eficaz, a análise de dados seria mais lenta, mais propensa a erros e menos fiável."* [cite: 74]
