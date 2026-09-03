# 🏦 Bank Term Deposit Subscription Prediction

A machine learning project evaluating **Decision Tree**, **Random Forest**, and **XGBoost** classification models to predict whether a client will subscribe to a bank term deposit (*deposito*) based on the Bank Marketing dataset.

---

## 📌 Project Overview

Direct telemarketing campaigns are a primary channel for banks to promote term deposits, but contacting every client incurs significant time and operational costs. 

This project analyzes **4,521 customer records** to build supervised classification models that identify high-probability subscribers prior to outreach. By accurately targeting likely subscribers, banks can optimize marketing efficiency and maximize campaign conversion rates.

---

## 📊 Dataset Overview (`bank.csv`)

* **Dataset Size:** 4,521 records, 17 attributes (16 features + 1 target)
* **Delimiter:** Semicolon (`;`)
* **Target Variable:** `y` (`"yes"` = subscribed, `"no"` = did not subscribe)
  * Class Distribution: **4,000 "no" (88.5%)** vs. **521 "yes" (11.5%)** *(imbalanced dataset)*

### Feature Breakdown

| Category | Attribute | Description | Data Type |
| :--- | :--- | :--- | :--- |
| **Client Demographics** | `age` | Age of client | Numeric |
| | `job` | Job category (12 types: `admin.`, `blue-collar`, `technician`, etc.) | Categorical |
| | `marital` | Marital status (`married`, `single`, `divorced`) | Categorical |
| | `education` | Education level (`primary`, `secondary`, `tertiary`, `unknown`) | Categorical |
| **Financial Profile** | `default` | Has credit in default? (`yes`, `no`) | Categorical |
| | `balance` | Average yearly balance (in EUR) | Numeric |
| | `housing` | Has housing loan? (`yes`, `no`) | Categorical |
| | `loan` | Has personal loan? (`yes`, `no`) | Categorical |
| **Last Contact Data** | `contact` | Contact communication type (`cellular`, `telephone`, `unknown`) | Categorical |
| | `day` | Last contact day of the month | Numeric |
| | `month` | Last contact month of year (`jan`–`dec`) | Categorical |
| | `duration` | Last contact duration in seconds | Numeric |
| **Campaign Context** | `campaign` | Number of contacts performed during this campaign | Numeric |
| | `pdays` | Days passed after client was last contacted (-1 = not previously contacted) | Numeric |
| | `previous` | Number of contacts performed before this campaign | Numeric |
| | `poutcome` | Outcome of the previous marketing campaign (`unknown`, `other`, `failure`, `success`) | Categorical |

---

## ⚙️ Methodology & Modeling Workflow

1. **Exploratory Data Analysis (EDA):**
   * Analyzing target class imbalance (`88.5% no` vs `11.5% yes`).
   * Visualizing distributions for key numerical features (`duration`, `balance`, `age`).
2. **Data Preprocessing:**
   * Loading data with semicolon delimiter: `pd.read_csv('bank.csv', sep=';')`.
   * Categorical encoding (One-Hot Encoding / Ordinal Encoding).
   * Feature scaling using `StandardScaler`.
   * Train-Test split (80/20 split with stratification on target `y`).
3. **Model Training & Comparison:**
   * **Decision Tree Classifier:** Baseline interpretable decision model.
   * **Random Forest Classifier:** Ensemble bagging approach to reduce variance.
   * **XGBoost Classifier:** Advanced gradient boosting tuned for classification performance.
4. **Evaluation Metrics:** Accuracy, Precision, Recall, F1-Score, and ROC-AUC (focusing on Recall/F1-Score due to target imbalance).

---

## 📈 Model Performance & Results

| Model | Accuracy | ROC-AUC |
| :--- | :---: | :---: |
| **Decision Tree** | *0.85* | *0.67* |
| **Random Forest** | *0.89* | *0.95* |
| **XGBoost** | *0.93* | *0.97* |

---

## 📁 Repository Structure

```Deposito_Subscription_Prediction
├── bank.csv                     # Dataset (4,521 rows, semicolon-separated)
├── deposit_prediction.ipynb     # Main Colab Notebook
├── README.md                    # Project documentation