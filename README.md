# 🛡️ Fraud Detection in E-Commerce and Banking

## 📋 Project Overview

This project implements advanced machine learning models for fraud detection in two domains:

- **E-Commerce Transactions** – Fraud detection with geolocation and behavioral analysis
- **Credit Card Transactions** – Banking transaction fraud detection

The goal is to enhance transaction security by identifying fraudulent activities using data preprocessing, feature engineering, model training, and explainable AI (SHAP). The workflow is fully reproducible with DVC for large files and models.

---

## 🎯 Business Impact

- **Security Enhancement:** Real-time fraud detection
- **Risk Mitigation:** Reduced financial losses
- **Customer Trust:** Improved user experience, minimal false positives
- **Compliance:** Meets regulatory requirements

---

## 🏗️ Project Structure

```
fraud-detection-ecommerce-banking/
├── data/
│   ├── raw/           # Original datasets
│   ├── cleaned/       # Cleaned and engineered datasets
│   ├── trained/       # Trained models (DVC tracked)
│   └── SHAP/          # SHAP outputs (DVC tracked)
├── notebooks/
│   ├── 01_data_analysis_preprocessing.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_model_building.ipynb
│   └── shap_analysis.ipynb
├── src/               # Source code (future)
├── reports/           # Analysis reports (future)
├── .dvc/              # DVC config and cache
└── README.md
```

---

## 🚀 Installation & Setup

*
**Setup:**
```bash
git clone <repository-url>
cd fraud-detection-ecommerce-banking
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
dvc pull  # Download large files (models, SHAP outputs) if you have DVC remote access
```

---

## 📊 Project Workflow

### 1. Data Analysis & Preprocessing
- Data cleaning, validation, and type conversion
- Geolocation enrichment via IP mapping
- Feature engineering: temporal, behavioral, geolocation, categorical
- Class balancing with SMOTE and stratified train-test split

### 2. Model Building & Evaluation
- Models: Logistic Regression (interpretable), Random Forest (ensemble)
- Feature scaling and encoding
- Model evaluation: PR-AUC, F1, ROC-AUC, confusion matrix
- Model selection based on PR-AUC and interpretability

### 3. Model Explainability (SHAP)
- SHAP summary plots (global feature importance)
- SHAP force plots (local explanations)
- Insights for business and technical stakeholders

### 4. Reproducibility & Data Versioning
- All large files in `data/trained/` and `data/SHAP/` tracked with DVC
- Notebooks and code tracked with Git

---

## 📈 Results & Insights

- **E-commerce:** PR-AUC > 0.7, strong feature importance from Random Forest
- **Credit Card:** PR-AUC > 0.8, robust detection of rare fraud cases
- **SHAP:** Key features identified for both global and local explanations
- **Business:** Actionable insights for fraud prevention and risk mitigation

---

## 💾 Data & Model Management

- **Small files** (code, notebooks): Tracked with Git
- **Large files** (models, SHAP outputs): Tracked with DVC
- To fetch data/models:  
  `dvc pull`
- To push new results:  
  `dvc add data/trained data/SHAP`  
  `git add data/trained.dvc data/SHAP.dvc .gitignore`  
  `git commit -m "Track models and SHAP outputs with DVC"`  
  `git push`  
  `dvc push`

---

## 📂 Notebooks

- `01_data_analysis_preprocessing.ipynb` – Data cleaning and merging
- `02_eda.ipynb` – Exploratory data analysis
- `03_feature_engineering.ipynb` – Feature creation and transformation
- `04_model_building.ipynb` – Model training, evaluation, and export
- `shap_analysis.ipynb` – Model explainability with SHAP

---

