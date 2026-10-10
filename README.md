# 🏠 House Price Prediction (Regression Models)

## 📌 Project Overview
This project builds multiple machine learning regression models to predict house prices based on various features from the Ames Housing dataset.  
The workflow includes data cleaning, handling missing values, outlier treatment, feature engineering, encoding, scaling, model training, and evaluation.  

The final solution leverages *Voting Regressor* (combination of Linear Regression, Random Forest, Gradient Boosting, and XGBoost) to achieve the best performance.  

---

## 📂 Dataset
- *Name:* Ames Housing Dataset  
- *Source:* [Kaggle - House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data)  
- *Shape:* 1460 rows × 81 columns  

Target Variable:  
- *SalePrice* → House sale price (continuous variable)  

---

## ⚙ Steps & Methodology

### 1. Data Cleaning
- Checked for null values and duplicates  
- Imputed missing values based on domain logic:
  - Filled LotFrontage by median per neighborhood  
  - Categorical features with "None" where applicable  
  - Numerical features like GarageYrBlt, GarageArea filled with 0  
- Dropped rows with missing Electrical  

### 2. Outlier Handling
- Detected outliers using IQR method  
- Two approaches:
  - *Clipping* extreme values (e.g., LotArea, GrLivArea, GarageArea)  
  - *Removing* extreme outliers from key numeric features  

### 3. Exploratory Data Analysis (EDA)
- Correlation heatmap of top features vs SalePrice  
- Visualizations:
  - Boxplots & scatterplots of numeric vs target  
  - Barplots for categorical features (e.g., MSZoning, KitchenQual)  
  - SalePrice distribution analysis  

### 4. Feature Engineering
- Created new features:
  - TotalSF = 1stFlrSF + 2ndFlrSF + TotalBsmtSF  
  - Age = YrSold - YearBuilt  
  - RemodAge = YrSold - YearRemodAdd  

### 5. Encoding & Scaling
- Ordinal encoding for quality features (ExterQual, KitchenQual, etc.)  
- OneHot encoding for nominal categorical features  
- StandardScaler applied on numerical features  

### 6. Feature Selection
- LassoCV used for selecting most predictive features  
- Selected top 15 features (e.g., OverallQual, GrLivArea, YearBuilt, TotalBsmtSF)  

### 7. Modeling & Evaluation
Trained and evaluated multiple regression models using R², MAE, and RMSE:  

| Model | R² | MAE | RMSE |
|-------|------|---------|---------|
| Linear Regression | 0.9060 | 16066.43 | 21607.50 |
| Lasso Regression | 0.9060 | 16066.43 | 21607.50 |
| Random Forest | 0.8935 | 16058.62 | 23002.54 |
| Gradient Boosting | 0.9093 | 15368.06 | 21223.59 |
| XGBoost | 0.8996 | 15715.87 | 22337.78 |
| *Voting Regressor* | *0.9166* | *14503.50* | *20352.61* |

---

## 📊 Results & Insights
- The *Voting Regressor* achieved the best performance with *R² = 0.9166* and lowest error (MAE & RMSE).  
- Gradient Boosting also performed well individually.  
- Linear and Lasso regression had nearly identical performance, indicating effective feature scaling and selection.  

---

## 🛠 Tools & Libraries
- *Python*  
- *Pandas, NumPy* → Data manipulation  
- *Matplotlib, Seaborn* → Visualization  
- *Scikit-learn* → Preprocessing, Linear/Lasso Regression, Random Forest, Gradient Boosting, Voting Regressor  
- *XGBoost* → XGBRegressor  
- *Joblib* → Model saving  

---

## 🚀 How to Run
```bash
# Clone the repository
git clone https://github.com/habiba-10/house-price-prediction.git
cd house-price-prediction

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn xgboost joblib

# Run the notebook / script
jupyter notebook HousePricePrediction.ipynb


## How to Predict on New Data

To generate predictions on new test data using the trained model:

1. Make sure the following files exist in the project directory:
   - final_model.pkl (the trained model)
   - scaler.pkl (the scaler used during training)
   - features.pkl (the selected features list)
   - columns.pkl (the full set of training columns)
   - predict.py (the prediction script)

2. Place your test dataset as a CSV file (e.g., test020920251.csv) in the same folder.

3. Run the prediction script:
   ```bash
   python predict.py
