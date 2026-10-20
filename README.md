# Loan Default Risk Analysis & Prediction

**Machine Learning · Credit Risk Analytics · Tableau Dashboards · Financial Decision Support**

An end-to-end credit risk analytics project developed for the **Business Intelligence & Data Analytics Enterprise Practicum (EY Group)**. We analyze historical loan applications, build machine learning models to identify potential defaults, segment borrowers by risk, and translate the findings into interactive Tableau dashboards and actionable lending recommendations.

> **Project context:** Academic industry-practicum case study, presented June 13, 2025. The analysis and recommendations are not a production credit-scoring system.

## 🔗 Interactive Tableau Dashboards

| Dashboard | Link | Purpose |
| --- | --- | --- |
| Loan Risk Analysis | [Explore dashboard](https://public.tableau.com/app/profile/.55241275/viz/__17489663468710/__2) | Explore lending risk and borrower-level characteristics. |
| Risk Overview | [Explore dashboard](https://public.tableau.com/app/profile/.55241275/viz/riskoverview/RiskOverview2) | Review portfolio-level risk indicators and default patterns. |

The dashboard work covers **portfolio risk overview**, **default-factor analysis**, and **geographic/borrower characteristics**. Interactive filters support drill-down into borrower subgroups and their predicted risk distributions.

## 📌 Business Problem

The case focuses on a financial institution operating in **Michigan, Florida, and Texas**, where the observed loan default rate is elevated. Conventional review processes can require similar effort for applications with very different risk levels, while fragmented borrower information and missing values make oversight more difficult.

**Objectives**

- Predict the likelihood of loan default before lending decisions are made.
- Prioritize applications through interpretable **high-, medium-, and low-risk segments**.
- Identify influential borrower, credit, and historical-loan characteristics.
- Equip decision-makers with interactive dashboards for portfolio monitoring.
- Recommend differentiated reviews, periodic checks, and better data maintenance.

## 📊 Dataset at a Glance

| Measure | Value reported in project presentation |
| --- | --- |
| Observation period | December 2018 |
| Loan applications | Approximately 300,000 (307,507 shown in dashboard) |
| Defaulted loans | 24,825 |
| Observed default rate | **8.07%** |
| Original features | 124 |
| Features after preprocessing and engineering | **236** |

The data includes loan amounts and terms, external credit scores, income and employment, demographics, assets, family characteristics, historical borrowing, and data-completeness indicators. **Raw datasets are not included in the supplied project files**; notebook paths may need to be adapted to your environment.

## 🧠 Methodology

### 1. Data preparation and feature engineering

- Inspect missing values, variable types, distributions, and outliers.
- Remove selected low-value/high-missingness fields and impute eligible variables.
- Encode categorical variables and construct additional borrower and loan-history indicators.
- Engineer features such as active-loan ratios, overdue-loan measures, outstanding debt, credit-to-goods-price ratio, and interactions between borrower characteristics.
- Expand the feature set from **124 original variables to 236 modeled features**, as reported in the presentation.

### 2. Model experimentation

The prediction notebook investigates multiple approaches:

- Logistic Regression and Decision Trees as baselines
- XGBoost and **LightGBM** gradient-boosted models
- Class imbalance strategies, including undersampling and class weighting
- Hyperparameter tuning, decision thresholds, and evaluation with ROC-AUC, recall, precision, F1, and confusion matrices

The project emphasizes **recall of actual defaults**, given the business cost of failing to identify high-risk applications.

### 3. Explainability and segmentation

Feature-importance analysis highlights three particularly informative groups:

1. **External credit ratings**
2. **Loan characteristics**, including repayment and loan-to-asset indicators
3. **Previous borrowing history**, including outstanding credit and active loans

The notebooks also explore **SHAP explanations**, borrower group comparisons, and dimensionality-reduction visualizations. Risk segmentation uses an expected-loss-inspired score combining predicted default risk and loan amount, with percentile-based group boundaries in the presentation. This is a project-specific prioritization measure, not a fully calibrated regulatory expected-credit-loss calculation.

### 4. Visualization and business recommendations

Tableau dashboards communicate overall portfolio exposure, borrower segments, important default drivers, and geographic patterns. Suggested operational applications include risk-based review queues, targeted audits, enhanced checks for higher-risk applications, and improved borrower-data quality controls.

<img width="1080" height="594" alt="Screenshot 2026-10-20 at 2 14 33 PM" src="https://github.com/user-attachments/assets/351d6604-7874-48cd-8b56-f854f74df485" />

<img width="1078" height="595" alt="Screenshot 2026-10-20 at 2 15 40 PM" src="https://github.com/user-attachments/assets/c68ab188-b7e5-426e-9776-1deb3f4aa3a5" />


## 🏆 Reported Results

| Metric | Test-set result |
| --- | ---: |
| **ROC-AUC** | **0.77** |
| **Default-class recall** | **78%** |
| True positives (defaults correctly flagged) | 2,897 |
| False negatives (defaults missed) | 827 |
| True negatives | 26,240 |
| False positives | 16,163 |

These figures are taken from the **June 2025 final presentation**, rather than from a fresh execution of the notebooks. The recall-oriented threshold flags many non-defaulting applications, so any operational use would need to consider review capacity, precision, fairness, and calibration.

## 🗂️ Repository Contents

```text
.
├── EY_prediction.ipynb     # Data cleaning, feature engineering, modeling and evaluation
├── EY_Risk_Group.ipynb     # Risk grouping, borrower comparisons and visual exploration
├── 0613 期末報告.pdf         # Final project presentation (Traditional Chinese)
└── README.md               # Project overview
```

## 🛠️ Tools & Technologies

**Python**, **pandas**, **NumPy**, **scikit-learn**, **XGBoost**, **LightGBM**, **imbalanced-learn**, **SHAP**, **Matplotlib**, **Seaborn**, **PCA**, **UMAP**, **Jupyter / Google Colab**, and **Tableau Public**.

## 🚀 Getting Started

1. Clone the repository and open the notebooks in Jupyter or Google Colab.
2. Install the relevant Python packages:

   ```bash
   pip install notebook pandas numpy scipy scikit-learn xgboost lightgbm imbalanced-learn shap matplotlib seaborn umap-learn category-encoders
   ```
3. Provide the **authorized source datasets** and update file paths in the notebooks. Some cells were written for Google Colab and mount Google Drive.
4. Run `EY_prediction.ipynb` to explore preprocessing, modeling, and risk prediction; then review `EY_Risk_Group.ipynb` for segment analysis and visualization.
5. Open the linked Tableau Public dashboards to explore the interactive outputs.

**Reproducibility note:** The notebooks contain experimental and archived sections, and depend on datasets/intermediate files not supplied here. They are research notebooks, not a guaranteed one-click pipeline. Review execution order and paths before running.

## 💡 Key Takeaways

- Predictive modeling can surface default risk patterns that are difficult to recognize through manual review alone.
- Credit scores, loan terms, and prior borrowing behavior are especially useful for differentiating risk.
- Segmenting applications supports **risk-based allocation of review effort**, rather than treating every application identically.
- Interactive dashboards make portfolio risk easier to inspect and communicate to nontechnical stakeholders.

## 👥 Project Team

沈文心 · 易旻虹 · 鍾采真 · 白圓智 · 梁一淳 · 李欣芮

*Business Intelligence & Data Analytics Enterprise Practicum — EY Group | June 2025*

## ⚠️ Disclaimer

This repository documents an academic analytical project. Predictions, risk categories, and recommended actions are illustrative; they should not be used as the sole basis for real-world credit decisions. Any deployment would require independent validation, privacy safeguards, bias and fairness assessment, regulatory review, and ongoing monitoring.
