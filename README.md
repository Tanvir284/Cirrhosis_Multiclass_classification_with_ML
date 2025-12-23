# Cirrhosis Multiclass Classification with Machine Learning

This project implements a complete **end-to-end machine learning pipeline** for **multiclass classification of liver cirrhosis severity** using a **self-generated dataset**.  
The repository demonstrates data preprocessing, exploratory analysis, feature engineering, model training, evaluation, and interpretation using classical machine learning techniques.

---

## 📌 Project Highlights

- Multiclass classification problem (medical domain)
- **Self-generated dataset** (not copied from Kaggle or UCI)
- Complete ML lifecycle implemented in a Jupyter Notebook
- Multiple classical ML models compared
- Clear evaluation using standard classification metrics
- Reproducible and well-structured pipeline

---

## 🎯 Problem Statement

Cirrhosis is a chronic liver disease that progresses through multiple severity stages.  
The objective of this project is to **predict the severity class of cirrhosis** based on patient-level clinical features using supervised machine learning.

**Task type:** Multiclass classification  
**Input:** Tabular clinical features  
**Output:** Cirrhosis severity class (integer label)

---

## 🧪 Dataset Description (Self-Generated)

⚠️ **Important:**  
The dataset used in this project is **self-generated**. It was not collected from public medical repositories.  
This demonstrates the ability to design datasets, define feature semantics, and control distributions for modeling.

### Dataset Characteristics

- Data format: Tabular (CSV)
- Samples: Synthetic / curated
- Target variable: `cirrhosis_class`
- Classes: Multiple discrete severity levels

### Example Features

- Age  
- Sex  
- Liver enzyme levels (AST, ALT)  
- Bilirubin  
- Albumin  
- Platelet count  
- INR  
- Additional clinical indicators  

All preprocessing and transformations are documented in the notebook.

---

## 🔁 End-to-End Machine Learning Pipeline

```mermaid
flowchart TD
    A[Self-Generated Dataset] --> B[Data Cleaning & Validation]
    B --> C[Exploratory Data Analysis]
    C --> D[Feature Engineering]
    D --> E[Train / Test Split]
    E --> F[Model Training]
    F --> G[Model Evaluation]
    G --> H[Model Selection]


Cirrhosis_Multiclass_classification_with_ML/
│
├── cirrhosis-multiclass-classification-with-ml.ipynb
├── data/
│   ├── raw_data.csv
│   └── processed_data.csv
│
├── models/
│   └── trained_model.pkl
│
├── results/
│   ├── confusion_matrix.png
│   └── feature_importance.png
│
├── requirements.txt
└── README.md

1. Clone Repository
git clone https://github.com/Tanvir284/Cirrhosis_Multiclass_classification_with_ML.git
cd Cirrhosis_Multiclass_classification_with_ML
2. Create Virtual Environment
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate

3. Install Dependencies
pip install -r requirements.txt

4. Run Notebook
jupyter notebook


Open cirrhosis-multiclass-classification-with-ml.ipynb and run all cells.

📦 Dependencies

Python 3.8+

pandas

numpy

scikit-learn

matplotlib

seaborn

jupyter




Limitations

Dataset is synthetic / self-generated (not clinical-grade)

Results should not be used for real medical diagnosis

External validation with real patient data is required

🚀 Future Improvements

Train with real-world clinical datasets

Apply advanced ensemble and boosting techniques

Add SHAP / LIME for model explainability

Deploy model using FastAPI or Flask

Perform hyperparameter optimization with Optuna

👤 Author

Tanvir Islam
BSc in Computer Science & Engineering (AI Major)
GitHub: https://github.com/Tanvir284

📄 License

This project is licensed under the MIT License.
