# Salifort Motors — Employee Turnover Prediction

A predictive employee turnover model built with Logistic Regression, Decision Tree, and Random Forest, developed as the final Capstone project for the **Google Advanced Data Analytics Professional Certificate**.

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-data%20wrangling-150458?logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-modeling-F7931E?logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-benchmark-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-notebook-F37626?logo=jupyter&logoColor=white)

---

## The business problem

**Salifort Motors**, a fictional alternative-energy vehicle manufacturer with over 100,000 employees, faces a high turnover rate, driving recurring recruitment and training costs. HR wants to understand **why employees leave** and **flag who's at risk of leaving**, so the company can act before a resignation rather than after one.

This project answers both questions by building classification models on a dataset of **14,999 employees** and **10 self-reported features** (satisfaction, performance review score, project load, hours worked, tenure, salary, and more).

## Key results

| Model | AUC | Precision | Recall | F1-score | Accuracy |
|---|---|---|---|---|---|
| Logistic Regression | — | 79% | 82% | 80% | 82% |
| Decision Tree | 95.6% | 83.1% | 90.3% | 86.5% | 95.3% |
| **Random Forest** | **93.4%** | **91.3%** | **90.4%** | **88.5%** | **96.6%** |

Random Forest was selected as the final model for delivering the most consistent balance across metrics, even though the Decision Tree reached a marginally higher AUC.

## What the data shows

- **Workload is the strongest predictor of attrition.** Number of concurrent projects, monthly hours, and tenure carry the highest feature importance across both tree-based models.
- **Two distinct attrition profiles emerge:** low-satisfaction employees early in their tenure, and high-performing employees who are overworked and leave despite strong evaluations.
- **The four-year mark is a critical inflection point.** Employees around that tenure show a sharp drop in satisfaction, pointing to a likely career-progression bottleneck.
- **Every employee with 7 concurrent projects left the company** — a near-deterministic risk signal surfaced during exploratory analysis.
- **Promotions are rare and barely correlated with workload**, reinforcing the idea that recognition and growth aren't keeping pace with effort.

## Technical approach

**Data cleaning:** identified and removed 3,008 duplicate records (~20% of the dataset), handled outliers in `tenure` via quartile analysis, and standardized column names.

**Preventing data leakage:** early versions of the tree-based models scored high enough to raise suspicion of data leakage. `average_monthly_hours` was replaced with a derived feature (`overworked`, employees averaging above 175h/month), and `satisfaction_level` was dropped from the training set in the final models — making the predictions more realistic for a production scenario.

**Modeling:** Logistic Regression as an interpretable baseline; Decision Tree and Random Forest tuned via `GridSearchCV` with cross-validation. Since the classes are imbalanced (83% stayed / 17% left), evaluation prioritized Precision, Recall, F1-score, and ROC-AUC over accuracy alone.

## Tech stack

`Python` · `pandas` · `numpy` · `scikit-learn` · `XGBoost` · `matplotlib` · `seaborn` · `Jupyter Notebook`

## Repository structure

```text
├── data/
│   └── HR_comma_sep.csv
│
├── notebooks/
│   └── Salifort_Motors_Capstone.ipynb
│
├── reports/
│   ├── Salifort Motors Documento PACE.pdf
│   └── Salifort Motors Sumário Executivo.pdf
│
└── README.md
```

## Documentation

- 📑 [PACE Strategy Document](reports/Salifort%20Motors%20Documento%20PACE.pdf) — project planning, business objectives, and strategy, following the **PACE (Plan, Analyze, Construct, Execute)** framework.
- 📊 [Executive Summary](reports/Salifort%20Motors%20Sumário%20Executivo.pdf) — key findings and business recommendations in non-technical language, aimed at stakeholders.

## Running it locally

```bash
git clone https://github.com/nogsposito/salifort-motors-retention-analysis
cd salifort-motors-turnover
pip install pandas numpy scikit-learn xgboost matplotlib seaborn jupyter
jupyter notebook notebooks/Salifort_Motors_Capstone.ipynb
```

## Next steps

- Apply **SHAP** to interpret individual model predictions.
- Explore **K-Means** clustering to identify distinct at-risk employee profiles.
- Benchmark final performance against **XGBoost**.
- Investigate additional features: commute distance, work arrangement (remote/on-site), and bonus history.

---

Developed as part of the **Google Advanced Data Analytics Professional Certificate**.
