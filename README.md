# 🛒 CHURNBR – Pipeline de Machine Learning para Churn em E-commerce

Este projeto é o MVP de Ciência de Dados desenvolvido por mim como parte do curso da PUC-Rio. O objetivo foi construir um pipeline completo, reprodutível e orientado a negócio para **prever churn de clientes** em e-commerce, utilizando **Google Colab**, **scikit-learn** e boas práticas de ML (pipelines, validação, tuning e seleção de limiar).

> **Notebook (abrir no Colab):**  
> [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/wallace91x/ecommerce-churn-mvp-machine-learning/blob/main/notebooks/mvp_churn_ecommerce.ipynb)

---

## 🧠 Objetivo do Projeto

Identificar clientes com alta probabilidade de **churn** e apoiar ações de retenção. O projeto responde a perguntas-chave:

- Quais modelos e pré-processamentos alcançam melhor desempenho?  
- Qual **limiar de decisão** maximiza **recall** sem perder precisão de forma crítica?  
- Qual o **impacto financeiro** (ROI) ao acionar clientes com base nas previsões (parâmetros de negócio **C**, **V**, **R**)?

---

## 🚀 Stack Utilizada

- **Python (Google Colab)**
- **pandas, numpy, matplotlib, seaborn**
- **scikit-learn** (Pipeline, ColumnTransformer, GridSearchCV, métricas, curvas ROC/PR)
- **kagglehub** (ingestão automática do dataset)
- **joblib** (persistência opcional de artefatos)

---

## 📂 Estrutura do Projeto

| Pasta / Arquivo                                 | Descrição                                                                 |
|--------------------------------------------------|---------------------------------------------------------------------------|
| `notebooks/mvp_churn_ecommerce.ipynb`            | Notebook principal com ingestão, EDA leve, modelagem e avaliação         |
| `requirements.txt`                               | Dependências para reprodução                                             |
| `.gitignore`                                     | Regras para não versionar dados/modelos grandes                           |
| `README.md`                                      | Este arquivo com visão geral do projeto                                   |

> O dataset é baixado em runtime via **kagglehub**; a pasta `data/` não é versionada.

---

## 🔄 Etapas do Projeto

### 1. 📥 Ingestão e Organização
- Fonte: **Ecommerce Customer Churn Analysis and Prediction** (Kaggle), via `kagglehub`.  
- Checagens iniciais, mapeamento de tipos e **split estratificado 60/20/20** (treino/validação/teste) evitando vazamento.

### 2. 🧼 Preparação e Pré-processamento
- Imputação de ausentes, tratamento de outliers, seleção de atributos úteis.  
- **`ColumnTransformer`**: numéricos (imputação + *scaler*) e categóricos (One-Hot).  
- Tudo dentro de **Pipeline** para garantir reprodutibilidade.

### 3. 🏗️ Modelagem e Tuning
- **Baseline** com Dummy para referência.  
- Modelos comparados: **KNN**, **DecisionTree**, **NaiveBayes**, **SVM (RBF)**.  
- **GridSearchCV** (ROC AUC como *scoring*), *seeds* fixas e tabela de **tempos de treino**.

### 4. 🎯 Limiar de Decisão & Negócio
- Comparação de limiares: **padrão (0.50)**, **F2 (~0.29)** e **meta (~0.223)**.  
- Função de **ROI paramétrico** com entrada do usuário:  
  - **C** = custo de contato por cliente,  
  - **V** = valor monetário médio do cliente,  
  - **R** = taxa de recuperação (sucesso da ação).  
- Cálculo de **Lucro, Receita salva, Custos** e **Custo Implícito do FN** para suportar decisão.

### 5. 📊 Avaliação e Validação
- Métricas: **Acurácia, Precisão, Recall/Sensibilidade, Especificidade, ROC AUC**.  
- **Curvas ROC e Precision–Recall** (validação e teste) e **matriz de confusão**.  
- Seleção do modelo/limiar com melhor equilíbrio para o objetivo de **retenção**.

---

## 📈 Resultados Visuais

- Curvas **ROC** e **Precision–Recall** (comparação entre modelos e no teste)  
- **Matriz de confusão** no teste  
- Tabela comparativa de métricas e **tempos de treino** por modelo

---

## 💬 Conclusões

- O melhor desempenho global foi do **SVM (RBF)**; com limiar **F2 ≈ 0,29** priorizamos **Recall** (retenção) mantendo boa **Precisão**.  
- No **teste**, desempenho típico observado: **AUC ≈ 0,981**, **Acc ≈ 0,950**, **Prec ≈ 0,805**, **Recall ≈ 0,932**, **Spec ≈ 0,954** (churn ≈ 16,8%).  
- A análise de **ROI** com parâmetros de negócio (ex.: **C=R$3,50**, **V=R$260**, **R=25%**) indicou **lucro positivo** ao acionar clientes de alto risco.  
- Pipeline é reprodutível (seeds fixas, *pipelines*, *split* estratificado) e facilmente extensível (ex.: calibrar probabilidades, testar XGBoost/LightGBM, *cost-sensitive learning*).

---

## 📄 Licença

Este projeto possui fins acadêmicos. O uso dos dados e do código é permitido mediante atribuição ao autor.

---

## 👨‍💻 Autor

**Wallace Lima**  
Ciência e Análise de Dados | Engenharia de Dados | Finanças | Compliance  
[LinkedIn](https://www.linkedin.com/in/wallacelima17/)
