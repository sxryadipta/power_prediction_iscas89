# A Comparative Study of Interpretable Machine Learning Models for Power Estimation of VLSI Circuits.

Comparing classical ML models for gate-level power estimation on ISCAS'89 benchmark circuits.

Includes:
- SVR
- KNN
- Random Forest
- XGBoost
- BPNN

and SHAP-based feature importance analysis because black-box models are annoying.

---

## What this project does

This project studies how different machine learning models perform on predicting power consumption in VLSI benchmark circuits using structural gate-level features.

The main focus was not just prediction accuracy, but also:
- interpretability
- feature importance
- model behavior across circuit complexity levels

Tree-based models performed best overall, especially XGBoost and Random Forest.

---

## Dataset

ISCAS'89 sequential benchmark circuits.

| Split | Circuits | Features |
|---|---|---|
| Train | 20 | 9 |
| Test | 5 | 9 |

LOOCV has also been used as it is a more reliable metric.

### Features
- gate
- and
- inv
- nor
- nand
- or
- dff
- in
- out

### Target
Power consumption (in log scale of Watts. This helps to normalize the distribution).

---

## Models Used

| Model | Notes |
|---|---|
| SVR | RBF kernel |
| KNN | k=5 |
| Random Forest | 500 trees |
| XGBoost | 200 estimators |
| BPNN | 2 hidden layers |

---

## SHAP Analysis

SHAP was used on XGBoost and Random Forest models to understand which structural parameters contribute most to power prediction.

Main finding:
- total gate count dominates prediction importance by a huge margin

Both tree models showed very similar parameter rankings, which makes the result more reliable instead of model-specific.

---

## Evaluation Strategy

The dataset is tiny (`n=25`), so normal train/test evaluation alone is misleading.

LOOCV (Leave-One-Out Cross-Validation) was used alongside the standard split to get more stable estimates.

---

## Project Structure

```bash
├── data/
├── notebooks/
├── results/
├── requirements.txt
└── README.md
```

Notebook pipeline:

```bash
01_setup_and_data.ipynb
02_eda.ipynb
03_preprocessing.ipynb
04_model_training.ipynb
05_shap_analysis.ipynb
06_complexity_analysis.ipynb
07_results_summary.ipynb
```

---

## Quickstart

```bash
pip install -r requirements.txt
```

Then run the notebooks in order.

Everything runs on CPU.
No GPU needed.
Total runtime is under ~2 minutes.

---

## Generated Results

The notebooks automatically generate:
- model comparison plots
- SHAP visualizations
- complexity-wise evaluation
- LaTeX-ready tables
- publication figures (300 DPI)

Outputs are stored inside:

```bash
results/
```

---

## Paper

**Title:**  
A Comparative Study of Interpretable Machine Learning Models for Power Estimation of VLSI Circuits.

Currently prepared for conference submission.

---

## Why I made this

Started as a VLSI + ML exploration project and slowly turned into:
- model comparison
- interpretability study
- tiny-dataset evaluation experiment
- me fighting SHAP plots for multiple evenings
