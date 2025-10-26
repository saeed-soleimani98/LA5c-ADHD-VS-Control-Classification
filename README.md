

## 🧠 Project Description

This repository accompanies our study on **explainable machine learning for ADHD classification using task-evoked and resting-state fMRI data** from the [OpenNeuro ds000030 (UCLA CNP)](https://openneuro.org/datasets/ds000030/versions/00016) dataset.
We developed a transparent, reproducible pipeline that integrates **Extreme Gradient Boosting (XGBoost)** and **Linear Discriminant Analysis (LDA)** models to distinguish between ADHD and control participants based on functional connectivity features derived from multiple cognitive paradigms — including **Stop-Signal Task (SST)**, **Spatial Capacity Task (SCAP)**, and **Resting State**.

### 🔍 Core Contributions

* **Explainable AI (XAI):** Utilized **SHAP (SHapley Additive Explanations)** to interpret model decisions at both the global and individual levels, offering neurobiologically meaningful insights.
* **Multimodal Integration:** Combined task-evoked and resting-state connectivity to capture dynamic neural signatures of cognitive control and attention.
* **Biologically Informed Findings:** Identified reproducible alterations in **fronto-parietal** and **cingulum–motor** networks—especially during inhibitory control (SST_Stop)—as potential candidate biomarkers for ADHD.
* **Transparent Workflow:** Includes fully documented preprocessing, feature construction, and model evaluation scripts for reproducibility and open science compliance.

### 💡 Scientific Impact

This work demonstrates how **interpretable machine learning** can bridge the gap between predictive modeling and neural mechanism understanding.
By linking classifier features to known executive-control circuitry, our results provide evidence for **task-based neuroimaging** as a dynamic, biologically grounded alternative to resting-state approaches in psychiatric research.

### 📊 Methods Overview

* **Data Source:** OpenNeuro ds000030 (UCLA CNP)
* **Features:** ROI-to-ROI functional connectivity matrices across multiple tasks
* **Models:** XGBoost (DART booster) and LDA (with RFECV feature selection)
* **Explainability:** SHAP-based global, local, and interaction analyses
* **Outputs:** Classification metrics (ROC-AUC, PR-AUC), confusion matrices, and SHAP visualizations

### ⚙️ Applications

The pipeline supports:

* Biomarker discovery in ADHD and other neuropsychiatric disorders
* Evaluation of connectivity-based diagnostic models
* Integration of explainable AI into neuroimaging workflows

### 📚 Citation

If you use this repository or its code in your research, please cite the forthcoming preprint once available.

---


