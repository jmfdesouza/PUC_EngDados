Pontifícia Universidade Católica - PUC Rio de Janeiro

Detecção de Fraudes Financeiras em Transações Bancárias: Um Pipeline de Dados na Nuvem

Este projeto tem como objetivo construir um pipeline de dados completo na nuvem para detecção de fraudes em transações bancárias utilizando aprendizado de máquina. A solução foi desenvolvida como Trabalho de Conclusão da pós-graduação em Engenharia de Dados, seguindo todas as etapas de coleta, modelagem, carga, análise e documentação.

---

Objetivo

Detectar transações financeiras fraudulentas com base em um conjunto de dados sintético disponível no Kaggle. Este projeto busca responder as seguintes perguntas:

1. Quais variáveis mais influenciam na ocorrência de fraudes?
2. Qual é a acurácia de modelos de machine learning na detecção de fraudes nesse conjunto de dados?
3. É possível reduzir falsos positivos sem comprometer a taxa de detecção de fraudes?
4. O pipeline é eficiente para fluxos em ambientes de nuvem?

---

Plataforma e Ferramentas Utilizadas

- **Google Colab** (desenvolvimento e prototipação)
- **Google Drive** (armazenamento dos dados)
- **Apache Spark via PySpark** (processamento distribuído)
- **Databricks Community Edition** (execução em nuvem)
- **GitHub** (repositório e versionamento)

---

Coleta de Dados

O dataset foi obtido no Kaggle:

- Link: [https://www.kaggle.com/datasets/ealaxi/paysim1](https://www.kaggle.com/datasets/ealaxi/paysim1)
- Licença: [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)
- Armazenamento: Google Drive sincronizado com Google Colab

---

Modelagem dos Dados

Utilizou-se uma modelagem em formato flat, típica de um **Data Lake**. Cada linha representa uma transação financeira com suas respectivas características.

Catálogo de Dados

| Coluna        | Descrição                                   | Tipo    | Intervalo/Categorias              |
|---------------|---------------------------------------------|---------|-----------------------------------|
| `step`        | Tempo em horas desde a primeira transação   | Int     | 1–744                             |
| `type`        | Tipo de transação                           | Categ.  | `CASH_OUT`, `PAYMENT`, etc.       |
| `amount`      | Valor da transação                          | Float   | 0.0–9,244,401.0                   |
| `oldbalanceOrg`| Saldo original do remetente                | Float   | 0.0–9,244,401.0                   |
| `newbalanceOrig`| Novo saldo do remetente                   | Float   | 0.0–9,244,401.0                   |
| `isFraud`     | Flag de fraude                              | Binário | 0 ou 1                            |

---

Carga e ETL

O pipeline de carga foi implementado utilizando:

- **PySpark** para transformação e manipulação dos dados;
- **Google Colab** com integração ao **Google Drive**;
- Os dados foram limpos, filtrados e normalizados;
- Utilizou-se técnicas de balanceamento de classes com `SMOTE`.

---

Análise de Dados

Qualidade dos Dados

- Dados sem valores nulos ou inconsistências.
- Detectou-se desbalanceamento severo entre classes (`isFraud` 0 ≫ 1).
- Foram aplicadas análises estatísticas descritivas e gráficos para validação da distribuição.

Solução do Problema

- O modelo de **Random Forest** foi treinado com os dados pré-processados.
- Métricas de desempenho:
  - **Acurácia**: 99,96%
  - **Recall** (fraude): 88,70%
  - **Precision** (fraude): 91,60%
- A análise identificou o tipo de transação e o valor como variáveis mais importantes.

