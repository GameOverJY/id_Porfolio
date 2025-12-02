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

[cite_start]A disciplina funciona num regime de avaliação contínua (peso 100%), exigindo uma nota mínima final de **47.5%** para aprovação[cite: 1180, 1181].

* [cite_start]**Portfólio Digital (40%):** Registo contínuo da aprendizagem e evolução individual[cite: 1183].
* [cite_start]**Trabalho/Projeto Final (40%):** Projeto prático individual com defesa[cite: 1183].
* [cite_start]**Trabalho em Sala (20%):** Participação e realização de tarefas propostas nas aulas[cite: 1183].

---

## 💾 Fundamentos de Dados

[cite_start]O objetivo central da integração é garantir uma "Single Source of Truth" (Fonte Única da Verdade), unificando dados de sistemas dispersos[cite: 1001, 1002].

### Classificação de Dados
* [cite_start]**Estruturados:** Organizados em esquemas rígidos (tabelas SQL, CSV)[cite: 1044, 1047].
* [cite_start]**Semi-estruturados:** Com organização interna mas sem esquema fixo (JSON, XML)[cite: 1056, 1058].
* [cite_start]**Não Estruturados:** Dados complexos que exigem técnicas avançadas (imagens, PDFs, e-mails)[cite: 1071, 1073].

### Arquiteturas
* [cite_start]**Batch (Em Lote):** Processamento de grandes volumes em intervalos agendados (ex: ETL noturno)[cite: 1114, 1116].
* [cite_start]**Streaming (Tempo Real):** Processamento contínuo para baixa latência e decisão imediata[cite: 1131, 1134].
* [cite_start]**APIs:** Integração via serviços web (REST, SOAP) para comunicação entre sistemas[cite: 1151, 1153].

---

## 🔄 O Processo ETL (Extract, Transform, Load)

[cite_start]O ETL é o método padrão para preparar dados para análise e Business Intelligence (BI)[cite: 17, 39].

### 1. Extração (Extract)
[cite_start]Recolha de dados de fontes variadas[cite: 133].
* [cite_start]**Carga Completa (Full Load):** Extrai todos os dados; mais simples, mas mais pesado[cite: 163].
* [cite_start]**Carga Incremental:** Extrai apenas as alterações; mais eficiente para produção[cite: 165].

### 2. Transformação (Transform)
[cite_start]Fase onde se aplica a lógica de negócio e limpeza[cite: 210, 224].
* [cite_start]**Limpeza:** Tratamento de valores nulos e erros[cite: 224].
* [cite_start]**Padronização:** Uniformização de formatos (ex: datas)[cite: 225].
* [cite_start]**Enriquecimento:** Criação de novos dados derivados ou calculados[cite: 256].

### 3. Carga (Load)
[cite_start]Carregamento no destino final[cite: 296].
* [cite_start]**Data Warehouse:** Repositório de dados estruturados otimizado para consulta[cite: 299].
* [cite_start]**Data Lake:** Repositório que armazena grandes volumes de dados brutos[cite: 301].

---

## ⚔️ ETL vs. ELT

[cite_start]A arquitetura ELT inverte a ordem para tirar partido da *Cloud* e do *Big Data*[cite: 354, 366].

| Característica | ETL (Tradicional) | ELT (Moderno) |
| :--- | :--- | :--- |
| **Sequência** | Extrair $\to$ Transformar $\to$ Carregar | [cite_start]Extrair $\to$ Carregar $\to$ Transformar [cite: 354] |
| **Transformação** | Ocorre num servidor intermédio (staging). | [cite_start]Ocorre dentro do Data Warehouse de destino[cite: 367]. |
| **Cenário Ideal** | [cite_start]Dados estruturados e complexos[cite: 389]. | [cite_start]Grandes volumes (*Big Data*) e ingestão rápida[cite: 419, 421]. |

---

## 🛠️ Ferramentas de Integração

### Ferramentas Visuais (GUI)
[cite_start]Permitem criar fluxos "arrastar e soltar"[cite: 448]:
* [cite_start]**Pentaho (PDI):** Open-source e muito robusta[cite: 459, 461].
* [cite_start]**Talend:** Gera código Java/SQL e foca na performance[cite: 476, 477].
* [cite_start]**Apache NiFi:** Focado em fluxo de dados em tempo real[cite: 490].

### ETL com Programação (Python)
[cite_start]Oferece flexibilidade máxima e é padrão em engenharia de dados[cite: 505, 518].
* [cite_start]**Pandas:** Biblioteca essencial para manipulação de DataFrames (limpeza, joins)[cite: 532].
* [cite_start]**SQLAlchemy:** Facilita a conexão com bases de dados SQL[cite: 543].
