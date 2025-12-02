# 📘 Revisão de Conteúdos e Fundamentos de ETL

**Data:** 07/10/2025
**Instituição:** ISEC - Instituto Superior de Engenharia de Coimbra
**Curso:** CTeSP em Tecnologias e Programação de Sistemas de Informação
**Professor:** João Leal

---

## 📝 Sumário da Aula

Nesta sessão, realizámos uma revisão transversal dos conteúdos abordados até ao momento na unidade curricular, focando no modelo de funcionamento da disciplina e nos pilares da Integração de Dados:

* **Modelo de Avaliação:** Estrutura da avaliação contínua e pesos das componentes (Portfólio, Projeto e Trabalho em Aula).
* **Fundamentos:** Tipologia de dados (Estruturados vs. Não Estruturados) e arquiteturas de integração.
* **Ciclo de Vida ETL:** Análise detalhada das fases de Extração, Transformação e Carga.
* **Paradigmas:** Comparação estratégica entre ETL e ELT.
* **Stack Tecnológico:** Ferramentas visuais (Pentaho) e programação (Python/Pandas).

---

## 🎓 Modelo de Avaliação

A disciplina funciona num regime de avaliação contínua (peso 100%), exigindo uma nota mínima final de **47.5%** para aprovação.

* **Portfólio Digital (40%):** Registo contínuo da aprendizagem e evolução individual.
* **Trabalho/Projeto Final (40%):** Projeto prático individual com defesa.
* **Trabalho em Sala (20%):** Participação e realização de tarefas propostas nas aulas.

---

## 💾 Fundamentos de Dados

O objetivo central da integração é garantir uma "Single Source of Truth" (Fonte Única da Verdade), unificando dados de sistemas dispersos.

### Classificação de Dados
* **Estruturados:** Organizados em esquemas rígidos (tabelas SQL, CSV).
* **Semi-estruturados:** Com organização interna mas sem esquema fixo (JSON, XML).
* **Não Estruturados:** Dados complexos que exigem técnicas avançadas (imagens, PDFs, e-mails).

### Arquiteturas
* **Batch (Em Lote):** Processamento de grandes volumes em intervalos agendados (ex: ETL noturno).
* **Streaming (Tempo Real):** Processamento contínuo para baixa latência e decisão imediata.
* **APIs:** Integração via serviços web (REST, SOAP) para comunicação entre sistemas.

---

## 🔄 O Processo ETL (Extract, Transform, Load)

O ETL é o método padrão para preparar dados para análise e Business Intelligence (BI).

### 1. Extração (Extract)
Recolha de dados de fontes variadas.
* **Carga Completa (Full Load):** Extrai todos os dados; mais simples, mas mais pesado.
* **Carga Incremental:** Extrai apenas as alterações; mais eficiente para produção.

### 2. Transformação (Transform)
Fase onde se aplica a lógica de negócio e limpeza.
* **Limpeza:** Tratamento de valores nulos e erros.
* **Padronização:** Uniformização de formatos (ex: datas).
* **Enriquecimento:** Criação de novos dados derivados ou calculados.

### 3. Carga (Load)
Carregamento no destino final.
* **Data Warehouse:** Repositório de dados estruturados otimizado para consulta.
* **Data Lake:** Repositório que armazena grandes volumes de dados brutos.

---

## ⚔️ ETL vs. ELT

A arquitetura ELT inverte a ordem para tirar partido da *Cloud* e do *Big Data*.

| Característica | ETL (Tradicional) | ELT (Moderno) |
| :--- | :--- | :--- |
| **Sequência** | Extrair $\to$ Transformar $\to$ Carregar | Extrair $\to$ Carregar $\to$ Transformar |
| **Transformação** | Ocorre num servidor intermédio (staging). | Ocorre dentro do Data Warehouse de destino. |
| **Cenário Ideal** | Dados estruturados e complexos. | Grandes volumes (*Big Data*) e ingestão rápida. |

---

## 🛠️ Ferramentas de Integração

### Ferramentas Visuais (GUI)
Permitem criar fluxos "arrastar e soltar":
* **Pentaho (PDI):** Open-source e muito robusta.
* **Talend:** Gera código Java/SQL e foca na performance.
* **Apache NiFi:** Focado em fluxo de dados em tempo real.

### ETL com Programação (Python)
Oferece flexibilidade máxima e é padrão em engenharia de dados.
* **Pandas:** Biblioteca essencial para manipulação de DataFrames (limpeza, joins).
* **SQLAlchemy:** Facilita a conexão com bases de dados SQL.
