# Rossmann Store Sales Prediction

This repository contains a complete machine learning pipeline for predicting daily sales for Rossmann drug stores using historical sales and store metadata. The solution leverages data preprocessing, feature engineering, exploratory data analysis, and an XGBoost regression model.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Data Description](#data-description)
- [Feature Engineering](#feature-engineering)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Modeling Approach](#modeling-approach)
- [Evaluation](#evaluation)
- [How to Run](#how-to-run)
- [File Structure](#file-structure)
- [Requirements](#requirements)
- [Acknowledgments](#acknowledgments)
- [License](#license)

---

## Project Overview

The goal is to forecast sales for each Rossmann store on each day in the test set. The project demonstrates a robust approach to handling real-world retail data, including missing values, categorical variables, and time-based features.

---

## Data Description

- **train.csv**: Historical daily sales data for each store, including:
  - `Store`: Store ID
  - `DayOfWeek`: Day of the week (1=Monday, 7=Sunday)
  - `Date`: Date of the record
  - `Sales`: Sales amount (target variable)
  - `Customers`: Number of customers (not available in test)
  - `Open`: Whether the store was open (0/1)
  - `Promo`: Whether the store was running a promotion
  - `StateHoliday`: Whether the day was a state holiday
  - `SchoolHoliday`: Whether the day was a school holiday

- **test.csv**: Data for which sales predictions are required (same columns as train except `Sales` and `Customers`).

- **store.csv**: Metadata for each store, including:
  - `StoreType`: Type of store (a, b, c, d)
  - `Assortment`: Level of product assortment
  - `CompetitionDistance`: Distance to nearest competitor
  - `CompetitionOpenSinceMonth`/`Year`: When competition opened
  - `Promo2`: Whether the store is running continuous promotions
  - `Promo2SinceWeek`/`Year`: When Promo2 started
  - `PromoInterval`: Months when Promo2 is active

- **sample_submission.csv**: Example of the required submission format.

---

## Feature Engineering

- **Date Features**: Extracted `Year`, `Month`, and `Day` from the `Date` column.
- **Categorical Encoding**: Label encoding for `StateHoliday`, `StoreType`, and `Assortment`.
- **Missing Value Imputation**: Filled missing values in competition and promo columns using median/mode or business logic.
- **Merging**: Combined `train`/`test` with `store` data for richer features.
- **Feature Selection**: Used mutual information regression to identify the most important features for predicting sales.

**Final Features Used:**
- Store
- DayOfWeek
- Open
- Promo
- StateHoliday (encoded)
- SchoolHoliday
- Year
- Month
- Day

---

## Exploratory Data Analysis

- Visualized sales distributions, store types, and the impact of promotions and holidays.
- Analyzed missing values and their patterns.
- Explored correlations between features and the target variable.

---

## Modeling Approach

- **Model**: XGBoost Regressor
- **Hyperparameters**:
  - n_estimators: 1000
  - learning_rate: 0.05
  - max_depth: 7
  - subsample: 0.8
  - colsample_bytree: 0.8
- **Training**: Used 80/20 train-validation split.
- **Evaluation Metrics**: Mean Absolute Error (MAE), R² Score.

---

## Evaluation

- The model was evaluated on a validation set using MAE and R².
- Feature importance was visualized using mutual information scores and XGBoost's built-in feature importance.

---

## Workflow

1. **Data Loading**: Read all CSV files into pandas DataFrames.
2. **Data Cleaning & Imputation**: Handle missing values and encode categorical variables.
3. **Feature Engineering**: Extract date features and merge store information.
4. **Exploratory Data Analysis**: Visualize distributions and relationships.
5. **Feature Selection**: Use mutual information to assess feature importance.
6. **Model Training**: Train an XGBoost regressor on the processed data.
7. **Prediction**: Generate predictions for the test set.
8. **Submission**: Save predictions in the required format.

---

## How to Run

1. **Clone the repository and place all data files (`train.csv`, `test.csv`, `store.csv`, `sample_submission.csv`) in the working directory.**
2. **Install requirements:**
   ```bash
   pip install numpy pandas seaborn matplotlib scikit-learn xgboost
   ```
3. **Open and run the notebook:**
   - `rossman (1).ipynb`
4. **The final predictions will be saved as:**
   - `xgboost_predictions.csv`

---

## File Structure

```
├── rossman (1).ipynb
├── train.csv
├── test.csv
├── store.csv
├── sample_submission.csv
├── xgboost_predictions.csv
├── README.md
```

---

## Requirements

- numpy
- pandas
- seaborn
- matplotlib
- scikit-learn
- xgboost

Install requirements with:
```bash
pip install numpy pandas seaborn matplotlib scikit-learn xgboost
```

---

## Acknowledgments

- [Kaggle Rossmann Store Sales Competition](https://www.kaggle.com/c/rossmann-store-sales)
- Rossmann Stores for the dataset

---

## License

MIT License

---
