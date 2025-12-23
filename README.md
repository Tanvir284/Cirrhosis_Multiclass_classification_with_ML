# 🏥 Cirrhosis Multiclass Classification with Machine Learning

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/Framework-Scikit--Learn-orange?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![ML](https://img.shields.io/badge/Models-XGBoost%20%7C%20LightGBM%20%7C%20CatBoost-green?style=for-the-badge)](https://github.com/dmlc/xgboost)
[![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)]()
[![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> **A high-performance machine learning pipeline designed to predict the survival status of patients with primary biliary cirrhosis using advanced ensemble techniques and probability calibration.**

---

## 📌 Executive Summary

This repository contains an end-to-end solution for a multiclass classification problem. The goal is to predict patient outcomes: **C** (Censored), **CL** (Censored due to Liver Transplant), or **D** (Death).

Using a **self-generated synthetic dataset** that mimics real-world medical data complexities, this project demonstrates a mastery of the full ML lifecycle—from robust feature engineering and Bayesian hyperparameter tuning to complex ensemble strategies and post-hoc probability calibration.

### 🌟 Key Technical Highlights
* **Bayesian Optimization:** Automated hyperparameter tuning using **Optuna** for Gradient Boosting models.
* **Advanced Encoding:** Implementation of **Out-of-Fold (OOF) Target Encoding** to handle high-cardinality categorical features without data leakage.
* **Ensemble Architecture:** A hybrid strategy combining **Stacking** (Meta-learning) and **Blending** (Weighted Averaging).
* **Probability Calibration:** Application of **Temperature Scaling** to align predicted probabilities with true occurrence rates, minimizing Log Loss.

---

## 🛠️ System Architecture & Workflow

The following flowchart illustrates the data processing and modeling pipeline implemented in the notebook.

```mermaid
graph TD
    subgraph Data_Ingestion
    A[Raw Self-Generated Dataset] --> B{Preprocessing Pipeline}
    end

    subgraph Feature_Engineering
    B --> C[Median/Mode Imputation]
    B --> D[Frequency Encoding]
    B --> E[OOF Target Encoding]
    B --> F[Interaction Features<br/>(Numeric Ratios)]
    end

    subgraph Model_Development
    C & D & E & F --> G[Feature Space X]
    G --> H[LightGBM + Optuna]
    G --> I[XGBoost + Optuna]
    G --> J[CatBoost + Optuna]
    G --> K[Base Learners<br/>(RF, ET, LogReg, KNN)]
    end

    subgraph Ensemble_Strategy
    H & I & J & K --> L{Ensembling}
    L --> M[Bagging Best Single Model]
    L --> N[Stacking<br/>(Meta-Learner: LogReg)]
    L --> O[Weighted Blending<br/>(Inverse LogLoss)]
    end

    subgraph Post_Processing
    M & N & O --> P[Temperature Scaling]
    P --> Q[Final Submission]
    end
