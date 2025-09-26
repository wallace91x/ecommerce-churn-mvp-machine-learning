# MVP – Churn em E-commerce (Classificação Supervisionada)

Pipeline reprodutível para predição de churn: ingestão via `kagglehub`, pré-processamento com `Pipeline/ColumnTransformer`, comparação de modelos (KNN, DecisionTree, NaiveBayes, SVM), ajuste de limiar (F2) e ROI paramétrico (C, V, R).

**Notebook (abrir no Colab):**  
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1bjbCIJo9XcMgTUq572rrQWiIRr9uaKsF#scrollTo=dlegMXzaNjDX)

## Como executar
1. Abra o link do Colab acima (ou rode localmente com `pip install -r requirements.txt`).
2. O dataset é baixado automaticamente em runtime via `kagglehub`.

## Resultados (resumo)
- Modelo final: **SVM (RBF)** com **threshold F2≈0,29**.
- TESTE: **AUC≈0,981**, **Acc≈0,950**, **Prec≈0,805**, **Recall≈0,932**, **Spec≈0,954**.
- ROI (exemplo): **C=R$3,50**, **V=R$260**, **R=25%** → **Lucro ≈ R$10.735**.

