# Rossmann Store Sales Prediction

This repository contains a machine learning solution for predicting daily sales for Rossmann drug stores using historical sales and store data.

## Project Overview

The goal is to forecast sales for each store on each day in the test set. The solution uses data preprocessing, feature engineering, and an XGBoost regression model.

## Data

- **train.csv**: Historical sales data for each store.
- **test.csv**: Data for which sales predictions are required.
- **store.csv**: Additional information about each store.
- **sample_submission.csv**: Example of the required submission format.

## Features Used

- Store
- DayOfWeek
- Open
- Promo
- StateHoliday
- SchoolHoliday
- Year (extracted from Date)
- Month (extracted from Date)
- Day (extracted from Date)

## Workflow

1. **Data Loading**: Read all CSV files into pandas DataFrames.
2. **Data Cleaning & Imputation**: Handle missing values and encode categorical variables.
3. **Feature Engineering**: Extract date features and merge store information.
4. **Exploratory Data Analysis**: Visualize distributions and relationships.
5. **Feature Selection**: Use mutual information to assess feature importance.
6. **Model Training**: Train an XGBoost regressor on the processed data.
7. **Prediction**: Generate predictions for the test set.
8. **Submission**: Save predictions in the required format.

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