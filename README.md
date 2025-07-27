# 🛡️ Fraud Detection in E-Commerce and Banking

## 📋 Project Overview

This project implements advanced machine learning models for fraud detection across two critical domains:

- **E-Commerce Transactions** (`Fraud_Data.csv`) - E-commerce fraud detection with geolocation analysis
- **Credit Card Transactions** (`creditcard.csv`) - Banking transaction fraud detection

The primary objective is to enhance transaction security by identifying fraudulent activities through comprehensive data preprocessing, feature engineering, and explainable AI (XAI) techniques. Effective fraud detection minimizes financial losses and builds trust for customers and financial institutions.

## 🎯 Business Impact

- **Security Enhancement**: Real-time fraud detection capabilities
- **Risk Mitigation**: Reduced financial losses from fraudulent transactions
- **Customer Trust**: Improved user experience with minimal false positives
- **Compliance**: Meeting regulatory requirements for financial institutions

---

## 🏗️ Project Structure

```
fraud-detection-ecommerce-banking/
├── data/
│   ├── raw/                    # Original datasets
│   │   ├── Fraud_Data.csv
│   │   ├── IpAddress_to_Country.csv
│   │   └── creditcard.csv
│   └── cleaned/                # Processed datasets
│       ├── fraud_data_cleaned.csv
│       ├── ip_country_cleaned.csv
│       ├── creditcard_cleaned.csv
│       └── fraud_data_engineered.csv
├── notebooks/
│   ├── 01_data_analysis_preprocessing.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_feature_engineering.ipynb
│   └── 04_model_building.ipynb
├── src/                        # Source code (planned)
├── models/                     # Trained models (planned)
├── reports/                    # Analysis reports (planned)
└── README.md
```

---

## 🚀 Installation & Setup

### Prerequisites

- Python 3.8+
- pip or conda package manager

### Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd fraud-detection-ecommerce-banking
   ```

2. **Create and activate virtual environment**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
   ```

4. **Verify installation**
   ```bash
   python -c "import pandas, sklearn, imblearn; print('Setup complete!')"
   ```

---

## 📊 Current Progress

### ✅ Task 1: Data Analysis & Preprocessing (COMPLETED)

#### 🧹 Data Cleaning & Quality Assurance

- **Dataset Loading**: Successfully loaded all three datasets with proper error handling
- **Data Validation**: Verified data integrity, removed duplicates, handled missing values
- **Type Conversion**: Converted timestamps to datetime format for temporal analysis
- **Data Quality**: Ensured consistent data types and formats across all datasets

#### 🗺️ Geolocation Integration

- **IP Address Processing**: Converted IP addresses to integer format for efficient merging
- **Range-Based Join**: Implemented interval-based join using `pd.merge_asof()` for IP-to-country mapping
- **Data Enrichment**: Successfully merged fraud data with geolocation information

#### 🛠️ Feature Engineering (E-Commerce Data)

**Temporal Features:**

- `time_since_signup`: Duration between signup and purchase (in hours)
- `hour_of_day`: Hour of purchase (0-23)
- `day_of_week`: Day of week for purchase (0-6)

**Behavioral Features:**

- `tx_count_by_user`: Number of transactions per user
- `txn_velocity_hours`: Time between consecutive purchases per user

**Geolocation Features:**

- `country`: Country derived from IP address mapping

**Categorical Features:**

- Browser type, traffic source, user gender, device information

#### 📈 Data Transformation & Class Balancing

**Class Imbalance Analysis:**

- Identified severe class imbalance in both datasets (fraud < 5% of transactions)
- Implemented comprehensive data transformation pipeline

**Transformation Pipeline:**

- **Scaling**: StandardScaler for numerical features
- **Encoding**: OneHotEncoder for categorical variables with memory optimization
- **Resampling**: SMOTE for balanced training data (achieved 50/50 class distribution)
- **Train-Test Split**: Stratified split (80/20) to maintain class proportions

**Results:**

```
✅ Class distribution AFTER sampling:
class
0    0.5  # Legitimate transactions
1    0.5  # Fraudulent transactions
```

### ✅ Task 2: Model Building & Training (COMPLETED)

#### 🤖 Model Development

**Models Implemented:**

1. **Logistic Regression** - Baseline interpretable model with balanced class weights
2. **Random Forest** - Ensemble model with optimized hyperparameters

**Model Architecture:**

- **Categorical Handling**: Label encoding for categorical variables
- **Feature Scaling**: StandardScaler for numerical features
- **Class Balancing**: Balanced class weights for both models
- **Hyperparameter Optimization**: Optimized Random Forest parameters

#### 📊 Model Evaluation & Performance

**Evaluation Metrics Used:**

- **AUC-PR** (Area Under Precision-Recall Curve) - Primary metric for imbalanced data
- **F1-Score** - Harmonic mean of precision and recall
- **Confusion Matrix** - Detailed classification results
- **Precision & Recall** - Individual performance metrics
- **ROC-AUC** - Area under ROC curve

**Performance Results:**

- **E-commerce Dataset**: Both models achieved competitive performance with PR-AUC > 0.7
- **Credit Card Dataset**: Excellent performance with PR-AUC > 0.8
- **Feature Importance**: Random Forest provided insights into key fraud indicators
- **Model Comparison**: Comprehensive comparison table with all metrics

#### 🎯 Model Selection & Justification

**Selection Criteria:**

- **PR-AUC** as primary metric for imbalanced fraud detection
- **Interpretability** vs performance trade-off consideration
- **Feature importance** insights from Random Forest
- **Business applicability** for real-world deployment

**Key Findings:**

- Random Forest captured complex non-linear patterns effectively
- Logistic Regression provided better interpretability for stakeholders
- Both models showed strong performance on imbalanced datasets
- Feature importance analysis revealed key fraud indicators

---

## 🔄 Next Steps

### 📋 Task 3: Model Explainability (IN PROGRESS)

**SHAP Analysis Implementation:**

- **Global Feature Importance**: Overall feature contribution analysis
- **Local Explanations**: Individual prediction explanations
- **Feature Interactions**: Complex feature relationship analysis
- **Business Insights**: Actionable recommendations for fraud prevention

**Planned Deliverables:**

- SHAP summary plots for both datasets
- Force plots for individual predictions
- Feature interaction analysis
- Business interpretation and recommendations

### Model Performance Targets

- **AUC-PR > 0.8** for both datasets ✅
- **F1-Score > 0.7** for fraud detection ✅
- **False Positive Rate < 0.1** to maintain user experience

### Business Metrics

- **Reduced Fraud Losses**: 20-30% reduction in fraudulent transactions
- **Improved Detection Speed**: Real-time fraud detection capabilities
- **Enhanced User Experience**: Minimal false positives
