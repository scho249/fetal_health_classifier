# Fetal Health Classification using Machine Learning

## Overview

This project develops machine learning models to classify fetal health conditions using cardiotocography (CTG) data from the UCI Machine Learning Repository.

Cardiotocography is a clinical monitoring technique that records fetal heart rate and uterine contractions during pregnancy. However, interpretation of CTG signals is often subjective and prone to variability between clinicians.

This project aims to improve diagnostic consistency and accuracy through machine learning.

---

## Objective

The primary objective is to accurately classify fetal health into three categories:

- **Normal (N)**
- **Suspicious (S)**
- **Pathologic (P)**

Special emphasis is placed on:

> **Minimizing false negatives for the Pathologic class**

---

## Dataset

- Source: UCI Machine Learning Repository (https://archive.ics.uci.edu/dataset/193/cardiotocography)
- Dataset: Cardiotocography  
- Samples: 2,126  
- Features used: 20 physiological variables  

---

## Data Preprocessing

### Data Cleaning
- No missing values detected or removed
- Verified all features are numeric

### Feature Selection
- Removed highly correlated features (threshold: 0.9)
- Dropped **Median** due to redundancy

### Feature Scaling
- Applied to standardize feature ranges

### PCA (Optional)
- Reduced dimensionality to **11 components (90% variance)**

---

## Handling Class Imbalance

Original training distribution:

N: 1323  
S: 236  
P: 141  

After applying **SMOTE**:

N: 1323  
S: 1323  
P: 1323  

---

## Models Evaluated

### PCA-based Models
- Logistic Regression
- SVM (Linear, RBF)
- KNN

### Non-PCA Models
- Decision Tree
- Random Forest
- Gradient Boosting
- AdaBoost
- MLP

---

## Model Tuning

- Focused on:
  - Random Forest
  - Gradient Boosting

- Used:
  - RandomizedSearchCV
  - Custom scoring (Recall for Pathologic class)

---

## Results

### Best Model: Gradient Boosting

| Metric        | Score  |
|--------------|--------|
| Accuracy      | 0.9507 |
| F1 Macro      | 0.9217 |
| F1 Weighted   | 0.9506 |
| Recall Macro  | 0.9239 |

### Insights

- **Normal (N)**: 97% correctly classified  
- **Pathologic (P)**:
  - 97% correctly classified  
  - 3% misclassified as Normal  
  - 0% misclassified as Suspicious  
- **Suspicious (S)**:
  - 83% correctly classified  

---

## Conclusion

Gradient Boosting is selected as the final model due to its strong overall performance and high recall for Pathologic cases.

---

## Tech Stack

- Python
- scikit-learn
- imbalanced-learn
- pandas, numpy
- matplotlib, seaborn

---

## 👤 Author

Claire Cho  
