

# 🧠 Explainable Machine Learning for ADHD Classification Using Task and Resting-State fMRI

### 📘 Overview

This repository contains the full analysis pipeline and results for our study on **explainable machine learning for ADHD classification** using **task-evoked and resting-state fMRI data** from the [OpenNeuro ds000030 (UCLA CNP)](https://openneuro.org/datasets/ds000030/versions/00016) dataset.
We benchmarked multiple machine learning algorithms to classify **ADHD vs. control** participants based on **ROI-to-ROI functional connectivity** features across several cognitive tasks.

Among all tested models, **XGBoost** and **Linear Discriminant Analysis (LDA)** achieved the most reliable performance and highest interpretability, supported by SHAP-based explainability and feature-level insights.

---

## 🎯 Research Objective

The goal of this project is to identify **neurobiologically interpretable functional connectivity biomarkers** of ADHD using **transparent and reproducible machine learning methods**.
The pipeline combines **multimodal task-based and resting-state fMRI** data, advanced **model evaluation**, and **explainable AI (XAI)** to uncover neural mechanisms of attention and cognitive control.

---

## 🧩 Dataset

* **Source:** [OpenNeuro ds000030 (UCLA Consortium for Neuropsychiatric Phenomics)](https://openneuro.org/datasets/ds000030/versions/00016)
* **Participants:** ADHD and control subjects
* **Tasks:**

  * **SST (Stop-Signal Task):** inhibitory control
  * **SCAP (Spatial Capacity Task):** working memory
  * **Resting-State:** baseline functional connectivity
* **Feature extraction:** ROI-to-ROI correlation matrices exported via the **CONN Toolbox**, aggregated across conditions into a unified feature space (~60 features per subject).

---

## ⚙️ Methods and Pipeline

### 🧠 Preprocessing and Feature Engineering

* Functional connectivity (ROI × ROI) extracted for REST, SST-Go, SST-Stop, and SCAP conditions.
* All features standardized and merged into a single feature matrix with diagnostic labels.
* Features correspond to functional coupling between key regions (e.g., **precuneus–SMA**, **middle frontal–precentral**).

### 🤖 Models Evaluated

| Algorithm            | Type              | Key Traits                         | Interpretability |
| -------------------- | ----------------- | ---------------------------------- | ---------------- |
| **XGBoost (DART)**   | Gradient Boosting | High accuracy, robust to imbalance | High (via SHAP)  |
| **LDA (SVD Solver)** | Linear Classifier | Simple and fast                    | High             |
| Random Forest        | Ensemble          | Stable baseline                    | Medium           |
| SVM                  | Kernel            | Sensitive to scaling               | Medium           |
| Logistic Regression  | Linear            | Baseline benchmark                 | Medium           |
| kNN                  | Instance-based    | Non-parametric                     | Low              |

**Top Models:**

* **XGBoost** achieved the highest predictive accuracy and stability across folds.
* **LDA** provided consistent and interpretable linear separability.

---

## 🔍 Explainability and Interpretation

We used **SHAP (SHapley Additive Explanations)** to understand model decision patterns at both the **global** and **subject** levels.

* **Global SHAP summary plots:** revealed the most discriminative connections for ADHD diagnosis.
* **Individual SHAP force plots:** highlighted subject-level heterogeneity in connectivity patterns.
* **LDA coefficient maps:** confirmed similar fronto-parietal and cingulum–motor involvement.

**Key neural biomarkers:**

* Reduced **precuneus–SMA** coupling during inhibitory control (SST_Stop).
* Altered **middle frontal–precentral** connectivity during working memory (SCAP).
* Network-level dysfunctions across **fronto-parietal** and **cingulum–motor** circuits linked to ADHD symptomatology.

---

## 📊 Repository Structure and Outputs

### Folder Organization

```

  📁 final_results/
      ├── 📁 lda_pub_results/
      │    ├── lda_cv_10fold_mean_ci.csv
      │    ├── lda_feature_coefficients.csv
      │    └── 📁 figs/  → LDA confusion matrices, ROC curves
      │
      ├── 📁 lda_saved_models/
      │    └── lda_pipeline.joblib
      │
      ├── 📁 xgb_pub_results/
      │    ├── cv_10fold_mean_ci.csv
      │    ├── feature_importance_gain.csv
      │    ├── feature_importance_cover.csv
      │    ├── feature_importance_weight.csv
      │    └── 📁 figs/  → SHAP plots, feature importance, confusion matrix
      │
      ├── 📁 xgb_saved_models/
      │    └── 📁 xgb_model_YYYYMMDD_HHMMSS/
      │         ├── xgb_booster.json
      │         ├── xgb_booster.ubj
      │         ├── xgb_pipeline.joblib
      │         └── metadata.json
```

### Output Descriptions

| Output File                                   | Description                                                                         |
| --------------------------------------------- | ----------------------------------------------------------------------------------- |
| `cv_10fold_mean_ci.csv`                       | Cross-validation performance metrics (mean accuracy, ROC-AUC, confidence intervals) |
| `feature_importance_gain.csv`                 | Gain-based XGBoost feature importance                                               |
| `feature_importance_cover.csv`                | Frequency-based feature importance                                                  |
| `feature_importance_weight.csv`               | Raw feature contribution weights                                                    |
| `lda_feature_coefficients.csv`                | Linear discriminant coefficients for each feature                                   |
| `xgb_pipeline.joblib` / `lda_pipeline.joblib` | Serialized model pipelines for reproduction                                         |
| `xgb_booster.ubj`                             | Native XGBoost model object (binary format for deployment)                          |
| `figs/`                                       | Figures: SHAP summary plots, ROC curves, confusion matrices, and feature rankings   |

All trained models and results can be easily reloaded for validation, visualization, or publication.

---

## 🧬 Key Results Summary

| Model                 | Accuracy (CV) | ROC-AUC   | Notes                                  |
| --------------------- | ------------- | --------- | -------------------------------------- |
| **XGBoost**           | High          | Excellent | Best performing, strong generalization |
| **LDA**               | Moderate–High | Good      | Best interpretability                  |
| Random Forest         | Moderate      | Fair      | Used for feature selection             |
| Others (SVM, LR, kNN) | Variable      | Lower     | Benchmark baselines                    |

---

## 🧠 Interpretation and Impact

This project demonstrates that **task-based connectivity**, when combined with explainable models, yields interpretable biomarkers for ADHD.
It supports a **distributed network dysfunction** model, linking **executive control**, **attention**, and **motor** systems in ADHD.
The results underscore the value of **XAI** and **reproducible ML** pipelines in clinical neuroimaging research.

---

## ⚖️ Ethics and License

* **Dataset:** Publicly available, anonymized (OpenNeuro ds000030).
* 
* **No identifiable data** included in this repository.
* 
* **License:** MIT — free for academic and non-commercial use with attribution.

---

## 🧾 Citation

> **Title:** Explainable Machine Learning for ADHD Classification Using Task-Evoked and Resting-State fMRI
> 
> **Authors:** [soleimani] et al.
> 
> **Dataset:** OpenNeuro ds000030 (UCLA CNP)
> 
> **Status:** Manuscript under review
> 
> **License:** MIT

Please cite this repository and upcoming preprint when using these models or scripts.



Would you like me to now create a **README header section** (with badges for Python, license, dataset DOI, and environment) so your GitHub page looks professional and ready for public release?
