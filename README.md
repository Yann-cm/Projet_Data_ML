# Projet_Data_ML# Chargeback Fraud Challenge

## 📌 Project Overview

This project was developed as part of the **Chargeback Fraud Challenge**.

The objective is to build a **binary classification model** to detect accounts at risk of fraud or chargeback.

The model must predict:

- `target_is_fraud = 1` → Fraud / chargeback risk  
- `target_is_fraud = 0` → Normal behavior  

The evaluation metric is the **F1-score on the positive class (fraud)**.  
Since the metric depends on the decision threshold, we use predicted probabilities and select an optimal threshold based on validation results.

---

```
## 🏗 Project Structure
.
├── 1.EDA/               # Exploratory Data Analysis
├── 2.Proces/            # Preprocessing pipeline
├── 3.modelisation/      # Modeling experiments
├── 4.Models/            # Saved final model
├── 5.Preds/             # For your prediction
├── 6.Data/              # Train & Test datasets
├── 7.Submission/        # Final submission file
└── README.md
```

---

## 🚀 How To Run the Project

### 1️⃣ Place the Data
Put train and test files inside: 6.Data/


With correct names.

---

### 2️⃣ Run Preprocessing
Execute: 2.Proces/Preprocess_FInale.ipynb


This prepares the data.

---

### 3️⃣ Train the Model (Optional if using saved model)

Run: 3.modelisation/XG_Boots_model_Finale.ipynb


---

### 4️⃣ Generate Predictions

Use the trained model to:

- Predict probabilities
- Apply optimal threshold
- Export submission file
---


## 🔎 Project Workflow

### Step 1 — Exploratory Data Analysis (EDA)

Folder: `1.EDA/`

The EDA phase allows us to:

- Understand variable distributions
- Detect missing values
- Identify outliers
- Analyze correlations
- Detect multicollinearity
- Analyze categorical variables
- Study class imbalance
- Identify potentially redundant or suspicious features

The EDA directly guides the preprocessing strategy.

---

### Step 2 — Data Preprocessing

Folder: `2.Proces/`

File: `Preprocess_FInale.ipynb`

This notebook:

- Cleans missing values
- Handles outliers
- Encodes categorical variables
- Processes date features
- Removes redundant variables
- Performs feature engineering
- Prepares data for modeling

⚠️ This step must be executed before training or testing the model.

---

### Step 3 — Model Training & Tuning

Folder: `3.modelisation/`

Contains:

- `baseline.ipynb`
- `XG_Boots_model_Finale.ipynb`

Here we:

- Train classification models
- Use cross-validation
- Tune hyperparameters
- Optimize for F1-score
- Perform threshold optimization using validation probabilities

The final selected model is based on best validation performance.

---

### Step 4 — Final Model Saving

Folder: `4.Models/`

File: XG_Boost_final.pkl


This file contains the trained model saved using pickle.

It can be reloaded to generate predictions without retraining.

---

### Step 5 — Data Placement

Before running the project:

1. Download the dataset
2. Place the files inside: 6.Data/



Rename them as:

- `kaggle_b2_fraud_train_v4`
- `kaggle_b2_fraud_test_v4`

The project expects these exact filenames.

---

### Step 6 — Generating Predictions

After:

1. Running preprocessing
2. Training the model (or loading the saved model)

You can:

- Generate predictions on the test set
- Apply the selected probability threshold
- Create the final submission file

The submission file must be saved in: 7.Submission/submission.csv


---

## 🎯 Threshold Selection Strategy

Since evaluation is based on **F1-score for class 1**, we:

1. Predict probabilities
2. Test multiple thresholds
3. Select the threshold maximizing F1-score on validation data

This ensures optimal fraud detection performance.

---

## 🔬 Robustness Considerations

Special attention was given to:

- Extremely correlated variables
- Potentially "too good to be true" features
- Data leakage risks
- Redundant encoded variables
- Stability of cross-validation results

The pipeline is designed to remain robust in realistic business conditions.


---


## 👥 Team & Methodology

The project follows a professional ML workflow:

EDA → Cleaning → Feature Engineering → Modeling → Validation → Threshold Optimization → Submission

---

## 📝 Conclusion

This project demonstrates:

- End-to-end machine learning pipeline
- Realistic fraud detection system
- Strong focus on evaluation metric optimization
- Robust preprocessing strategy
- Production-ready model saving and inference

---



## 📊 Dataset Description

The dataset is:

- Realistic and business-oriented
- Voluminous (~200,000 rows)
- Imperfect (like real-world data)
- Containing missing values, outliers, duplicates, and redundant variables

Each row represents a **customer account snapshot** at decision time.

### 🔹 Target Variable (Train Only)

- `target_is_fraud` (binary)
  - `1` = Fraud / chargeback risk
  - `0` = Normal account

---

### 🔹 Main Feature Categories

#### 1. Identifiers
- `customer_id`
- `account_id`  
(Not used for modeling)

#### 2. Demographics & Account Information
- `age`
- `tenure_months`
- `annual_income_eur`
- `credit_score`

#### 3. Transactional & Behavioral Features
- Transaction counts and amounts (30 days)
- Ratios (e.g. `max_to_avg_ratio`)
- Login activity
- Support interactions
- Historical chargebacks
- Failed payments

#### 4. Device & Risk Signals
- Device trust score
- IP risk score
- VPN usage
- New device detection
- Device type

#### 5. Geographic Information
- Country
- Region
- City
- Postal code

#### 6. Text Fields
- `last_ticket_subject`
- `customer_note`

#### 7. Additional Operational Signals
- Internal signals (`internal_signal_1` to `internal_signal_8`)
- Partner risk indicators
- Legacy risk scores
- Manual review results

#### 8. Date Feature
- `signup_date`

---
