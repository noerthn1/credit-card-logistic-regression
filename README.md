# 📌 Credit Card Default Prediction with Logistic Regression

## 🎯 Project Goal
Build a logistic regression model to predict **credit card default** using the UCI Credit Card dataset.  
Evaluate model performance, analyze feature importance, and explore threshold adjustments.

---

## 📂 Dataset
- Source: [UCI Machine Learning Repository – Default of Credit Card Clients Dataset](https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients)
- Size: 30,000 records, 24 features
- Target: `default.payment.next.month` (1 = default, 0 = non-default)

---

## ⚙️ Methods
1. **Data Preprocessing**  
   - Removed target from features (`X`), kept it in `y`.  
   - Train-test split (80/20).  

2. **Model Training**  
   - Logistic Regression with balanced class weights.  
   - Evaluated with confusion matrix, classification report, ROC-AUC.  

3. **Threshold Adjustment**  
   - Compared thresholds = 0.3, 0.4, 0.5.  
   - Metrics: Accuracy, Precision, Recall, F1.  

4. **Feature Importance**  
   - Extracted coefficients from logistic regression.  
   - Visualized top predictors of default.  

---

## 📊 Results

### Baseline (Threshold = 0.5)
- Accuracy: 69%  
- Precision (Default=1): 0.38  
- Recall (Default=1): 0.64  
- ROC-AUC: 0.728  

### Threshold Comparison
| Threshold | Accuracy | Precision | Recall | F1 |
|-----------|----------|-----------|--------|----|
| 0.3       | 0.36     | 0.24      | 0.90   | 0.38 |
| 0.4       | 0.55     | 0.31      | 0.77   | 0.44 |
| 0.5       | 0.69     | 0.38      | 0.64   | 0.48 |

👉 Lower thresholds increase recall (catch more defaulters) but reduce precision and accuracy.

### Feature Importance
Top 5 strongest predictors:  
1. `PAY_0` → late repayment last month (positive)  
2. `BILL_AMT1` → last bill amount (negative)  
3. `PAY_AMT2` → repayment amount two months ago (negative)  
4. `LIMIT_BAL` → credit limit (negative)  
5. `AGE` → slightly positive effect  

---

## 💡 Business Insights
- **Repayment history (`PAY_0`)** is the most critical factor in predicting default.  
- **Higher repayment amounts** and **larger credit limits** lower the chance of default.  
- **Threshold tuning** is key:  
  - At 0.5 → balanced performance.  
  - At 0.3 → bank identifies 90% of defaulters but misclassifies more safe clients.  
- In practice, banks may prefer **higher recall** (catching risky clients), even if false positives increase.

---

## 🚀 Next Steps
- Try more models (Random Forest, XGBoost).  
- Apply SMOTE or resampling for class imbalance.  
- Deploy with Streamlit/Flask for interactive demo.

---
