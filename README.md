# 📊 Arquitetura de Análise de Dados Híbrida: Sinergia entre BI e Python

> **Caderno Temático criado para o Desafio de Projeto da DIO (Digital Innovation One)**  
> *Curadoria e exploração realizadas via NotebookLM.*

---

## 🎯 1. Contexto e Objetivos

### Contexto
O projeto aborda a otimização de pipelines de dados corporativos integrando Python com Excel e Power BI para superar limitações técnicas tradicionais e maximizar a produtividade nas análises.

### Objetivos de Aprendizado
- [x] **Consumo de Modelos Semânticos:** Aprender a consumir modelos semânticos do Power BI dentro do Excel usando Python (`=PY()`).
- [x] **Tratamento de Dados Heterogêneos:** Automatizar a limpeza e o cruzamento de dados oriundos de múltiplas fontes (TXT, CSV, SQL) com a biblioteca Pandas.
- [x] **Avaliando Ferramentas de IA:** Analisar quais ferramentas de IA aumentam a produtividade em cada etapa do ciclo de vida dos dados.

---

## 📚 2. Curadoria de Fontes

Foram selecionados e carregados no NotebookLM 4 documentos estratégicos para embasar este caderno de estudos:

| Fonte / Documento | Descrição do Conteúdo |
| :--- | :--- |
| **Arquitetura Integrada de Análise de Dados** | Explica a sinergia e integração entre as quatro ferramentas fundamentais (Excel, SQL, Python e Power BI). |
| **Analyse Power BI data in Excel with Python** | Guia técnico (Chris Webb) focado no uso da função `=PY()` integrada a modelos semânticos. |
| **Python Integration in Power BI** | Guia prático para iniciantes cobrindo camadas de integração e tratamento estatístico de outliers. |
| **Diretrizes Estruturais e Governança em IA** | Documento focado nas melhores práticas, ferramentas modernas e governança/segurança no uso de IA para dados. |

---

## 🛠️ 3. Engenharia de Prompts & "Cicatrizes" (Troubleshooting)

Nesta seção estão documentadas as interações com a IA, incluindo refinamentos de prompt e aprendizados práticos obtidos com os erros.

### ❓ Perguntas Estratégicas Elaboradas
1. **Pergunta Inicial:** *"Como eu faria para analisar uma tabela com o Python e mesclar BD's?"*
   * **Objetivo:** Entender operações de `merge` e `concat` no Pandas.
2. **Prompt de Refinamento:** *"Como traduzir e cruzar dados de um dicionário para uma base em TXT?"*
   * **Objetivo:** Uso da função `pd.read_csv()` com diferentes separadores e mapeamento através de chaves/dicionários.

### 🩹 "Cicatrizes" (Percalços e Soluções)
* **Execução do Python no Excel:** A principal dificuldade foi compreender que o Python no Excel executa na nuvem (Microsoft Azure). Portanto, não é possível acessar arquivos locais diretamente sem passar os dados através da função/ponte `xl()`.
* **Limitação Visual do Power BI:** Identificou-se a limitação de **150.000 linhas** para visuais customizados em Python no Power BI. A solução documentada foi realizar agregações prévias no banco via SQL antes da renderização gráfica.

---

## 📘 4. Miniguia de Estudo (Entrega Final)

### 📖 Resumo Estruturado do Ciclo de Dados
* **Ingestão:** Utilizar SQL para grandes volumes estruturados e Python (com Regex) para arquivos não-estruturados ou semi-estruturados (ex: TXT).
* **Transformação:** Utilizar o Power Query para limpezas diárias/repetíveis e Python para análises estatísticas avançadas (Agrupamento via K-Means, Decomposição de Séries Temporais).
* **Visualização:** Priorizar visuais nativos no Power BI para interatividade, recorrendo a bibliotecas como Seaborn/Matplotlib apenas para gráficos complexos de correlação.

### 🧠 Glossário de Conceitos-Chave
* **Star Schema:** Modelo dimensional composto por tabelas Fato e Dimensão, ideal para performance em BI e consultas analíticas.
* **Semantic Link:** Recurso do Microsoft Fabric que permite ao Python ler metadados e medidas DAX diretamente no ambiente do Jupyter/Notebooks.
* **ETL (Extract, Transform, Load):** Processo fundamental de extração, tratamento e carga de dados entre diferentes sistemas.
* **Query Folding:** Capacidade do Power Query de converter etapas de tratamento em instruções SQL nativas, executando o processamento direto na fonte.

### 🔄 Prompts Reutilizáveis para Revisões Futuras
```text
1. "Atue como um analista de dados sênior. Explique a diferença de performance entre uma Coluna Calculada e uma Medida DAX em um modelo de 1 milhão de linhas."
2. "Escreva um script Python usando Pandas para realizar um left join entre as tabelas 'Vendas' e 'Dicionario' usando a coluna 'Cod_Prod' como chave."
3. "Quais são as melhores práticas de governança para usar o Copilot do Power BI em um ambiente corporativo?"
