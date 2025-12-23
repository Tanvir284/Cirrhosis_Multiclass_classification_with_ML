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
flowchart TD
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
📊 Methodology Detailed1. Data & PreprocessingThe dataset involves a mix of numerical biomarkers (e.g., Bilirubin, Albumin) and categorical demographics.Imputation: Handled missing values using Median strategies for continuous variables to be robust against outliers.Feature Generation:Created _missing_count to capture data quality patterns per patient.Generated ratio features (e.g., Bilirubin / Albumin) to capture physiological interactions.2. Advanced Feature EncodingTo maximize signal from categorical variables:Frequency Encoding: Captures the prevalence of categories.OOF Target Encoding: A sophisticated technique where categorical levels are replaced by the mean target value. Crucially, this is done inside a Cross-Validation loop (Out-of-Fold) to prevent the model from memorizing the target (leakage).3. Hyperparameter Tuning (Optuna)Instead of basic Grid Search, Optuna was utilized for Bayesian Optimization. This efficiently searches the hyperparameter space for LightGBM, XGBoost, and CatBoost, optimizing specifically for Multi-class Log Loss.4. Ensemble & CalibrationThe final prediction is not reliant on a single model.Stacking: A meta-model (Logistic Regression) learns how to best combine predictions from the base models.Blending: A weighted average where weights are inversely proportional to the validation Log Loss (better models get higher weight).Temperature Scaling: A post-processing step that scales the logits of the ensemble output to ensure the predicted probability distribution matches the true distribution, further reducing the Log Loss.📉 Results & PerformanceThe models were evaluated using Multi-class Log Loss and Accuracy. The ensemble approach demonstrated a significant improvement over individual models.ApproachMethodPerformance NoteBaselineSingle LightGBMStrong baselineTunedOptuna XGB/LGBM/Cat~5-10% improvement in Log LossEnsembleStacking + BlendingReduced variance and improved generalizationFinalCalibrated EnsembleBest recorded Log Loss💻 Getting StartedPrerequisitesPython 3.10+Jupyter Notebook / LabInstallationClone the repo:Bashgit clone [https://github.com/Tanvir284/Cirrhosis_Multiclass_classification_with_ML.git](https://github.com/Tanvir284/Cirrhosis_Multiclass_classification_with_ML.git)
Install dependencies:Bashpip install pandas numpy scikit-learn lightgbm xgboost catboost optuna matplotlib seaborn
Run the notebook:Bashjupyter notebook cirrhosis-multiclass-classification-with-ml.ipynb
🤝 ContributingContributions are welcome! Please feel free to submit a Pull Request.Fork the ProjectCreate your Feature Branch (git checkout -b feature/AmazingFeature)Commit your Changes (git commit -m 'Add some AmazingFeature')Push to the Branch (git push origin feature/AmazingFeature)Open a Pull Request📧 ContactTanvir - GitHub ProfileProject Link: https://github.com/Tanvir284/Cirrhosis_Multiclass_classification_with_ML
