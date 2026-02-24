# Modelo de Aprovação de Crédito (EDA → ML → Threshold por Custo)

Projeto end-to-end de **aprovação de crédito** com **EDA estruturado**, **modelagem consciente de leakage** e **calibração de threshold por custo** (política conservadora).

## 🔎 Visão geral
- **Alvo:** `loan_status` (1 = **aprovado**, 0 = negado)
- **Abordagem:** 5 etapas de EDA → benchmark de modelos → modelo final (XGBoost) → decisão operacional via threshold
- **Decisão:** threshold **0.89** (conservador), priorizando reduzir aprovações indevidas (**FP**) em troca de maior perda de oportunidade (**FN**)

---

## ✅ Principais entregas
- **EDA em 5 etapas:** perfil, risco, capacidade, produto e desfecho
- **Cenário “limpo” (sem leakage):** removemos `interest_rate` e `defaults_on_file`
- **Benchmark de ML:** LogReg, GradientBoosting, RandomForest, XGBoost e LightGBM
- **Modelo final:** **XGBoost** com alta performance e boa generalização
- **Threshold por custo:** otimizado com custo assimétrico (FP > FN), resultando em política conservadora
- **Baixo gap treino–validação–teste** no modelo final → boa generalização (sem sinais relevantes de overfitting)

---

## 📊 Resultados (cenário limpo)
- **ROC-AUC:** ~0.97  
- **PR-AUC:** ~0.98  
- **Threshold conservador (0.89):** **FP=118** (risco) | **FN=1793** (oportunidade perdida)

📌 **Notebook:** `notebooks/Loan_status.ipynb`  
📌 **Relatório (PDF):** `reports/Loan_status.pdf`

---

## 🖼️ Visualizações
### ROC Curves — Benchmark de Modelos
![ROC Curves](assets/roc_curves.png)

### Escolha de Threshold por Custo
![Threshold por custo](assets/threshold_cost.png)

### Trade-off: FP vs FN por Threshold
![FP vs FN](assets/tradeoff_fp_fn.png)

### Matriz de Confusão (Threshold = 0.89)
![Confusion Matrix](assets/confusion_matrix.png)

---

## 📁 Estrutura do repositório
- `notebooks/` → notebook principal do projeto
- `reports/` → relatório em PDF (versão para leitura rápida)
- `assets/` → imagens usadas no README

---

## 🧠 Dataset
O dataset está no Kaggle (não versionado no repositório):
```text
https://www.kaggle.com/datasets/parthpatel2130/realistic-loan-approval-dataset-us-and-canada/data
