# 📘 Ferramentas de Integração e Ecossistema ETL

**Data:** 28/10/2025  
**Instituição:** ISEC - Instituto Superior de Engenharia de Coimbra  
**Curso:** CTeSP em Tecnologias e Programação de Sistemas de Informação  
**Professor:** João Leal  

---

## 📝 Sumário da Aula

Nesta aula, explorámos o vasto ecossistema de ferramentas que suportam os processos de integração de dados. O foco incidiu na distinção entre soluções visuais e programáticas, bem como na evolução para ferramentas baseadas na Cloud e no paradigma ELT.

* **O Papel das Ferramentas:** Automação, abstração e gestão do ciclo de vida ETL.
* **Classificação:** Comparação entre soluções *Open Source* vs. Comerciais.
* **Critérios de Seleção:** Como escolher a ferramenta certa (Custo, Conectividade, Curva de Aprendizagem).
* **Panorama Tecnológico:**
    * **Open Source:** Pentaho (PDI), Apache NiFi, Apache Airflow.
    * **Comercial/Cloud:** Talend, SSIS, AWS Glue, Azure Data Factory.
    * **ELT Moderno:** Fivetran, dbt.
* **Abordagem Programática:** O uso de Python (Pandas/Requests) e SQL (Stored Procedures) para integrações personalizadas.

---

## 🛠️ O Papel das Ferramentas no ETL

As ferramentas de integração abstraem a complexidade da criação de *scripts* manuais, oferecendo interfaces gráficas (GUI) para:
1.  **Conectividade:** Ligação facilitada a múltiplas fontes (BDs, APIs, ERPs).
2.  **Transformação:** Aplicação visual de regras de limpeza e agregação.
3.  **Orquestração:** Agendamento e monitorização de fluxos de trabalho.

---

## ⚖️ Classificação e Critérios de Seleção

### Open Source vs. Comerciais
* **Open Source (ex: Pentaho, NiFi):** Gratuitas (licença), alta personalização, suporte via comunidade. Exigem maior *know-how* técnico.
* **Comerciais (ex: Informatica, SSIS):** Licenciamento pago, suporte dedicado, otimizadas para escala empresarial.

### Critérios de Escolha
Ao selecionar uma ferramenta, deve-se considerar:
* **Conectividade:** Suporta as nossas fontes de dados?
* **Escalabilidade:** Aguenta o volume de dados futuro?
* **Custo (TCO):** Licenças + Infraestrutura + Recursos Humanos.
* **Curva de Aprendizagem:** Facilidade de uso pela equipa existente.

---

## 🧰 Principais Ferramentas de Mercado

### 1. Ferramentas Open Source
* **Pentaho Data Integration (Kettle):** Focada em ETL tradicional *batch*. Interface visual intuitiva ("Spoon") para desenhar Transformações e Jobs.
* **Apache NiFi:** Especialista em fluxo de dados em tempo real (*dataflow*). Baseado em grafos e processamento contínuo.
* **Apache Airflow:** Plataforma de orquestração baseada em código (Python). Gere dependências complexas entre tarefas (DAGs).

### 2. Ferramentas Comerciais e Cloud
* **Talend:** Líder de mercado, gera código Java/SQL nativo.
* **Microsoft SSIS:** A escolha padrão para o ecossistema SQL Server/Windows.
* **Cloud Native (AWS Glue, Azure Data Factory):** Serviços *serverless* e geridos, ideais para *Big Data* e elasticidade.

### 3. Ferramentas ELT Modernas
Focadas em carregar dados brutos para a Cloud e transformar depois:
* **Fivetran/Stitch:** Automatizam a Extração e Carga (E+L).
* **dbt (data build tool):** Especialista na Transformação (T) usando SQL dentro do Data Warehouse.

---

## 💻 Integração com Código (Python & SQL)

Quando as ferramentas visuais não são suficientes ou o orçamento é limitado, a programação oferece flexibilidade total.

### SQL para Transformação
* **Views:** Camada de abstração virtual para simplificar consultas.
* **Stored Procedures:** Encapsulamento de lógica complexa de transformação executada diretamente no servidor de base de dados.

### Python para Extração de APIs
Uso da biblioteca `requests` para extrair dados da Web e `pandas` para estruturá-los.

#### Exemplo Prático: Extração de Taxas de Câmbio
Este *script* extrai dados de uma API, transforma-os num DataFrame e prepara-os para carga.

```python
import requests
import pandas as pd
from datetime import datetime

def extract_transform_exchange_rate(api_url):
    try:
        # 1. Extração (Extract)
        response = requests.get(api_url)
        response.raise_for_status() # Verifica erros HTTP
        data = response.json()

        # 2. Transformação (Transform)
        base = data.get('base')
        eur_rate = data.get('rates', {}).get('EUR')
        timestamp = datetime.now().strftime('%Y-%m-%d %H:%M:%S')

        if not eur_rate:
            return pd.DataFrame()

        # Criar DataFrame e aplicar regras de negócio
        df = pd.DataFrame({
            'Data': [timestamp],
            'Moeda_Base': [base],
            'Taxa_EUR': [eur_rate]
        })
        
        # Regra: Arredondar para 4 casas decimais
        df['Taxa_EUR'] = df['Taxa_EUR'].round(4)
        
        return df

    except Exception as e:
        print(f"Erro no pipeline: {e}")
        return pd.DataFrame()

# Execução
url = "[https://api.exchangerate-api.com/v4/latest/USD](https://api.exchangerate-api.com/v4/latest/USD)"
df_resultado = extract_transform_exchange_rate(url)
print(df_resultado)

