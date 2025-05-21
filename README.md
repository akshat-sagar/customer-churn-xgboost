# customer-churn-xgboost
Machine learning project to predict customer churn using XGBoost
# 📊 Customer Churn Prediction using XGBoost

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7%2B-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

Predicting customer churn using XGBoost with a dataset of behavioral metrics. Includes data cleaning, feature engineering, normalization, model training, and hyperparameter tuning using `GridSearchCV`.

---

## 📁 Dataset

The dataset `data1.csv` includes:
- 3333 rows
- 20 columns
- Features like session activity, clicks, purchases, support calls, etc.
- Target variable: `churn` (0 or 1)

---

## 🛠️ Installation

Clone this repository and install dependencies:

```bash
git clone https://github.com/your-username/churn-xgboost.git
cd churn-xgboost
pip install -r requirements.txt
```

### `requirements.txt`
```txt
pandas
numpy
xgboost
scikit-learn
```

---

## 🧹 Data Preprocessing

- Converted `"yes"/"no"` to `1/0`
- Cleaned float fields with commas (e.g. `"244,7" → 244.7"`)
- Converted `location code` to categorical using one-hot encoding
- Dropped non-informative columns like `user id`
- Scaled selected numerical columns with `Normalizer`

---

## 🚀 Model Training

- Split data with `train_test_split` (67% train / 33% test)
- Initial model trained with `XGBClassifier`
- Model Accuracy: **92%**

```python
from xgboost import XGBClassifier
model = XGBClassifier()
model.fit(x_train, y_train)
```

---

## 🔍 Hyperparameter Tuning

Used `GridSearchCV` for tuning:

```python
param_grid = {
    "max_depth": [5],
    "learning_rate": [0, 0.01, 0.05, 0.1],
    "gamma": [1, 5, 10],
    "scale_pos_weight": [2, 5, 10, 20],
    "subsample":[1],
    "colsample_bytree": [1]
}
```

### ✅ Best Parameters:
```python
{
    'colsample_bytree': 1,
    'gamma': 1,
    'learning_rate': 0.1,
    'max_depth': 5,
    'scale_pos_weight': 2,
    'subsample': 1
}
```

### 🎯 Final Accuracy: **92.5%**

---

## 📈 Evaluation Metric

- Accuracy Score: `sklearn.metrics.accuracy_score`
- Future suggestions:
  - Use F1-score and ROC-AUC for imbalanced data
  - Plot confusion matrix

---

## 📌 Features Used (after one-hot + scaling)

- Session durations
- App/desktop sessions & transactions
- Order values
- Click rates
- Support call frequency
- Discount/product view ratios
- Location code (one-hot encoded)

---

## 📦 Folder Structure

```bash
📁 churn-xgboost/
├── data1.csv
├── churn_model.ipynb
├── README.md
└── requirements.txt
```

---

## 🧠 Author

**[Akshat Sagar]**  
Inspired by churn analysis and real-world ML deployments.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## ⭐️ Show Your Support

If you found this helpful, give it a ⭐ on GitHub and feel free to fork!

