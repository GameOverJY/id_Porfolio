# 📘 Revisão de Conteúdos e Fundamentos de ETL

**Data:** 30/09/2025  
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

[cite_start]A disciplina funciona num regime de avaliação contínua (peso 100%), exigindo uma nota mínima final de **47.5%** para aprovação[cite: 990, 991].

* **Portfólio Digital (40%):** Registo contínuo da aprendizagem e evolução individual.
* **Trabalho/Projeto Final (40%):** Projeto prático individual com defesa.
* [cite_start]**Trabalho em Sala (20%):** Participação e realização de tarefas propostas nas aulas[cite: 993].

---

## 💾 Fundamentos de Dados

[cite_start]O objetivo central da integração é garantir uma "Single Source of Truth" (Fonte Única da Verdade), unificando dados de sistemas dispersos[cite: 1124].

### Classificação de Dados
* [cite_start]**Estruturados:** Organizados em esquemas rígidos (tabelas SQL, CSV)[cite: 1167].
* [cite_start]**Semi-estruturados:** Com organização interna mas sem esquema fixo (JSON, XML)[cite: 1179].
* [cite_start]**Não Estruturados:** Dados complexos como imagens, PDFs ou e-mails[cite: 1194].

### Arquiteturas
* [cite_start]**Batch (Em Lote):** Processamento de grandes volumes em intervalos agendados[cite: 1239].
* [cite_start]**Streaming (Tempo Real):** Processamento contínuo para baixa latência[cite: 1257].
* [cite_start]**APIs:** Integração via serviços web para comunicação entre sistemas[cite: 1274].

---

## 🔄 O Processo ETL (Extract, Transform, Load)

[cite_start]O ETL é o método padrão para preparar dados para análise e Business Intelligence (BI)[cite: 17].

### 1. Extração (Extract)
Recolha de dados de fontes variadas.
* **Carga Completa (Full Load):** Extrai todos os dados. [cite_start]Mais simples, mas pesado[cite: 163].
* **Carga Incremental:** Extrai apenas as alterações. [cite_start]Mais eficiente para produção[cite: 165].

### 2. Transformação (Transform)
Fase onde se aplica a lógica de negócio e limpeza.
* [cite_start]**Limpeza:** Tratamento de valores nulos e erros[cite: 224].
* [cite_start]**Padronização:** Uniformização de formatos (ex: datas)[cite: 225].
* [cite_start]**Enriquecimento:** Criação de novos dados derivados[cite: 256].

### 3. Carga (Load)
Carregamento no destino final.
* [cite_start]**Data Warehouse:** Repositório de dados estruturados para análise histórica[cite: 299].
* [cite_start]**Data Lake:** Repositório para dados brutos (Raw Data)[cite: 301].

---

## ⚔️ ETL vs. ELT

A arquitetura ELT inverte a ordem para tirar partido da *Cloud* e do *Big Data*.

| Característica | ETL (Tradicional) | ELT (Moderno) |
| :--- | :--- | :--- |
| **Sequência** | Extrair $\to$ Transformar $\to$ Carregar | Extrair $\to$ Carregar $\to$ Transformar |
| **Transformação** | Ocorre num servidor intermédio (staging). | [cite_start]Ocorre dentro do Data Warehouse de destino[cite: 367]. |
| **Cenário Ideal** | Dados estruturados e complexos. | [cite_start]Grandes volumes (*Big Data*) e ingestão rápida[cite: 419]. |

---

## 🛠️ Ferramentas de Integração

### Ferramentas Visuais (GUI)
Permitem criar fluxos "arrastar e soltar":
* [cite_start]**Pentaho (PDI):** Open-source e muito robusta[cite: 459].
* [cite_start]**Talend:** Gera código Java/SQL[cite: 476].
* [cite_start]**Apache NiFi:** Focado em fluxo de dados em tempo real[cite: 488].

### ETL com Programação (Python)

Oferece flexibilidade máxima.
* [cite_start]**Pandas:** Biblioteca essencial para manipulação de DataFrames (limpeza, joins)[cite: 532].
* [cite_start]**SQLAlchemy:** Facilita a conexão com bases de dados SQL[cite: 543].
