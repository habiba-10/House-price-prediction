# 🏠 House Price Prediction

This project is a **Machine Learning pipeline** for predicting house prices using the [Kaggle House Prices dataset](https://www.kaggle.com/code/emrearslan123/house-price-prediction).  
The workflow covers **data preprocessing, feature selection, model training, and evaluation**.

---

## 📌 Project Workflow

1. **Data Preprocessing**

   - Handle missing values
   - Encode categorical variables (Ordinal + One-Hot Encoding)
   - Scale numerical features using StandardScaler
   - Handle outliers (clipping & removal)

2. **Feature Selection**

   - Used **Lasso Regression (LassoCV)** for automatic feature selection.
   - Selected top 15 most important features.

3. **Models Implemented**

   - Linear Regression
   - Random Forest Regressor
   - Gradient Boosting Regressor

4. **Evaluation Metrics**
   - R² Score
   - MAE (Mean Absolute Error)
   - RMSE (Root Mean Squared Error)

---

## 📊 Results (using Lasso-selected features)

| Model             | R² Score | MAE      | RMSE     |
| ----------------- | -------- | -------- | -------- |
| Linear Regression | 0.9060   | 16066.43 | 21607.50 |
| Random Forest     | 0.8935   | 16058.62 | 23002.54 |
| Gradient Boosting | 0.9093   | 15368.06 | 21223.59 |

👉 **Gradient Boosting** gave the best performance.

---

## ⚙️ Installation & Usage

```bash
# Clone repository
git clone https://github.com/habiba-10/House-price-prediction.git
cd House-price-prediction

# Install required libraries
pip install -r requirements.txt
```
