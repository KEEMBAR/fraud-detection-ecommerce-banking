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
│   └── 03_feature_engineering.ipynb
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

---

## 🔄 Next Steps

### 📋 Task 2: Model Building & Training (IN PROGRESS)

**Planned Models:**

1. **Logistic Regression** - Baseline interpretable model
2. **Ensemble Model** - Random Forest or XGBoost/LightGBM

**Evaluation Metrics:**

- AUC-PR (Area Under Precision-Recall Curve)
- F1-Score
- Confusion Matrix
- Precision and Recall

### 📋 Task 3: Model Explainability (PLANNED)

**SHAP Analysis:**

- Global feature importance
- Local explanations for individual predictions
- Feature interaction analysis

---

## 🛠️ Technical Implementation

### Key Technologies Used

- **Data Processing**: Pandas, NumPy
- **Visualization**: Matplotlib, Seaborn
- **Machine Learning**: Scikit-learn, Imbalanced-learn
- **Feature Engineering**: Custom preprocessing pipelines
- **Version Control**: Git with organized branching strategy

### Performance Optimizations

- **Memory Management**: Sparse matrices for high-cardinality categorical variables
- **Efficient Joins**: Optimized IP range merging using sorted data
- **Scalable Pipelines**: Reusable transformation classes for production deployment

---

## 📈 Expected Outcomes

### Model Performance Targets

- **AUC-PR > 0.8** for both datasets
- **F1-Score > 0.7** for fraud detection
- **False Positive Rate < 0.1** to maintain user experience

### Business Metrics

- **Reduced Fraud Losses**: 20-30% reduction in fraudulent transactions
- **Improved Detection Speed**: Real-time fraud detection capabilities
- **Enhanced User Experience**: Minimal false positives

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📞 Contact

For questions or collaboration opportunities, please reach out to the project maintainers.

---

_Last updated: July 2024_
