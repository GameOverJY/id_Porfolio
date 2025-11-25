# 📘 Integração de Dados - Aula 02

**Data:** 16/09/2025
**Instituição:** ISEC - Instituto Superior de Engenharia de Coimbra
**Curso:** CTeSP em Tecnologias e Programação de Sistemas de Informação
**Professor:** João Leal

---

## 📝 Sumário da Aula

Nesta aula, aprofundámos os processos de movimentação e transformação de dados, com foco especial em ETL:

* **Definição de ETL:** Análise das fases de *Extract* (Extração), *Transform* (Transformação) e *Load* (Carregamento).
* **Contexto:** O papel do ETL em estratégias de *Data Warehousing* e *Business Intelligence* (BI).
* **Paradigmas:** Diferença concetual e prática entre **ETL** tradicional e **ELT** (Extract-Load-Transform).
* **Ferramentas:** Panorama das ferramentas de ETL de mercado e o uso de **Python** como linguagem de programação para engenharia de dados.

---

## 🏗️ Arquiteturas de Integração

Para compreender onde o ETL se encaixa, analisámos as diferentes arquiteturas de integração de dados e os seus requisitos de latência:

| Arquitetura | Descrição | Casos de Uso |
| :--- | :--- | :--- |
| **Batch (Em Lote)** | Processamento de grandes volumes de dados de forma agendada (ex: noturno). É aqui que o **ETL** é tradicionalmente usado. | Atualização de Data Warehouses, relatórios mensais, folhas de pagamento. |
| **Streaming (Tempo Real)** | Processamento contínuo, evento a evento. Baixa latência. | Deteção de fraudes, sensores IoT, monitorização de cliques. |
| **APIs / Serviços Web** | Integração via pedidos (requests) entre sistemas (REST, SOAP). | Apps móveis, gateways de pagamentos, consulta de stocks. |

---

## 📂 Tipos de Dados no Processo de Integração

O desafio do processo de "Transformação" (o T do ETL) reside frequentemente na necessidade de normalizar diferentes estruturas de dados:

1.  **Estruturados:** Organizados em tabelas/esquemas fixos (ex: SQL, CSV, Excel).
2.  **Semi-estruturados:** Sem esquema fixo, mas com organização interna (ex: JSON, XML, Logs).
3.  **Não estruturados:** Sem modelo definido, exigindo técnicas avançadas (ex: Imagens, PDFs, Vídeos).

---

## 🐍 ETL e Programação

Foi destacado o uso de **Código (Code-based ETL)** como alternativa ou complemento às ferramentas gráficas (GUI).

* **Linguagem de destaque:** Python.
* **Vantagens:** Flexibilidade total, bibliotecas poderosas para manipulação de dados (como Pandas) e facilidade de automação.
