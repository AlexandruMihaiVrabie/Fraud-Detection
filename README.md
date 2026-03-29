# Fraud Detection System

A machine learning project that detects fraudulent financial transactions using Logistic Regression, built with Python, scikit-learn, and Streamlit.

## 📋 Project Overview

This project analyzes a large dataset of financial transactions to build a fraud detection model. It includes:
- **Exploratory Data Analysis** (EDA) with visualizations
- **Feature Engineering** to create meaningful predictive features
- **Machine Learning Pipeline** using Logistic Regression
- **Streamlit Web App** for real-time fraud prediction

## 📁 Project Structure

```
fraud-detection/
│
├── AIML Dataset.csv              # Financial transactions dataset (~6M+ records)
├── analysis_model.ipynb          # Jupyter Notebook with full EDA, visualization & model training
├── fraud_detection.py            # Streamlit web app for real-time fraud prediction
├── fraud_detection_pipline.pkl   # Trained model pipeline (saved with joblib)
├── README.md                     # This file
└── requirements.txt              # Python dependencies (see installation)
```

## 🔍 Dataset

The dataset contains simulated financial transactions with the following features:

| Feature | Description |
|---|---|
| `type` | Transaction type (PAYMENT, TRANSFER, CASH_OUT, DEBIT, CASH_IN) |
| `amount` | Transaction amount |
| `nameOrig` | Sender customer ID |
| `oldbalanceOrg` | Sender's balance before the transaction |
| `newbalanceOrig` | Sender's balance after the transaction |
| `nameDest` | Receiver customer ID |
| `oldbalanceDest` | Receiver's balance before the transaction |
| `newbalanceDest` | Receiver's balance after the transaction |
| `isFraud` | Target variable (1 = fraud, 0 = legitimate) |
| `isFlaggedFraud` | System-flagged fraud indicator |

## 🚀 Installation & Setup

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/fraud-detection.git
cd fraud-detection
```

### 2. Create a virtual environment
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter streamlit joblib
```

### 4. Run the Jupyter Notebook
```bash
jupyter notebook analysis_model.ipynb
```

### 5. Run the Streamlit App
```bash
streamlit run fraud_detection.py
```

## 🧠 Model Details

- **Algorithm**: Logistic Regression with balanced class weights
- **Preprocessing Pipeline**:
  - `StandardScaler` for numerical features (amount, balances)
  - `OneHotEncoder` for categorical features (transaction type)
- **Train/Test Split**: 70% training / 30% testing (stratified)
- **Engineered Features**:
  - `balanceDiffOrg`: Difference between sender's old and new balance
  - `balanceDiffDest`: Difference between receiver's new and old balance

## 📊 Key Findings

- Fraud only occurs in **TRANSFER** and **CASH_OUT** transaction types
- The dataset is highly **imbalanced** (fraud represents < 1% of all transactions)
- Transactions where the sender's balance drops to **zero** are strong fraud indicators
- The `amount` feature has a moderate positive correlation with fraud

## 🌐 Streamlit Web App

The web app allows users to input transaction details and get an instant fraud prediction:

- Select the transaction type
- Enter the amount and balance information
- Click **Predict** to see if the transaction is potentially fraudulent

## 🛠️ Technologies Used

- **Python 3.14**
- **pandas** — Data manipulation
- **NumPy** — Numerical operations
- **Matplotlib & Seaborn** — Data visualization
- **scikit-learn** — Machine learning pipeline
- **Streamlit** — Web application framework
- **joblib** — Model serialization

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
