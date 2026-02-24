# Credit Approval Risk Model (EDA → ML → Cost-Based Threshold)

End-to-end credit approval project: robust EDA, leakage-aware modeling, and a cost-optimized conservative decision threshold.

## Project highlights
- **5-step EDA**: profile, risk, capacity, product and outcome (`loan_status`)
- **Leakage-aware**: trained a “clean” scenario without `interest_rate` and `defaults_on_file`
- **Model benchmark**: compared baseline models and tree-based ensembles; **XGBoost** performed best
- **Decisioning**: calibrated a **conservative threshold (0.89)** using a cost function (FP > FN)

## Results (clean scenario)
- ROC-AUC ≈ **0.97**
- PR-AUC ≈ **0.98**
- Conservative policy (threshold **0.89**): **FP=118**, **FN=1793** (risk vs opportunity trade-off)

## Repo structure
- `notebooks/` → main notebook
- `reports/` → PDF report

## Dataset
Dataset is hosted on Kaggle:
- Realistic Loan Approval Dataset (US & Canada)

## How to run
1. Download the dataset from Kaggle
2. Update the dataset path in the notebook (if needed)
3. Run `notebooks/Loan_status.ipynb`

## Notes
`loan_status=1` means **approved**.
