# Hackathon

# Airline Profitability Prediction

![Python Logo](https://www.python.org/static/community_logos/python-logo.png)  
![scikit-learn Logo](https://scikit-learn.org/stable/_static/scikit-learn-logo-small.png)  

This project aims to develop a high-performance machine learning model to predict airline profitability (in USD) based on a variety of operational and financial factors. The model is designed to provide accurate predictions while also offering interpretability, which helps airline operators understand the key drivers of profitability and optimize their decision-making processes.

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Methodology](#methodology)
  - [Data Preprocessing & Feature Engineering](#data-preprocessing--feature-engineering)
  - [Modeling](#modeling)
  - [Model Explainability](#model-explainability)
- [Results](#results)
- [Usage](#usage)
- [Requirements](#requirements)
- [Future Work](#future-work)
- [License](#license)

## Overview

Airline profitability is influenced by various factors such as flight delays, aircraft utilization, turnaround time, load factor, fleet availability, maintenance downtime, fuel efficiency, revenue, and operating costs. This project builds an ML pipeline that:

- Loads and preprocesses historical flight performance data.
- Engineers features to capture seasonal fluctuations and operational insights.
- Trains a robust model using Random Forest, tuned via hyperparameter optimization.
- Provides model explainability using SHAP to highlight the most influential factors on profitability.

## Dataset

The dataset used in this project contains historical flight performance data with approximately 200,000 records. The key features include:

- **Flight Number**
- **Scheduled Departure Time**
- **Actual Departure Time**
- **Delay (Minutes)**
- **Aircraft Utilization (Hours/Day)**
- **Turnaround Time (Minutes)**
- **Load Factor (%)**
- **Fleet Availability (%)**
- **Maintenance Downtime (Hours)**
- **Fuel Efficiency (ASK)**
- **Revenue (USD)**
- **Operating Cost (USD)**
- **Net Profit Margin (%)**
- **Ancillary Revenue (USD)**
- **Debt-to-Equity Ratio**
- **Revenue per ASK**
- **Cost per ASK**
- **Profit (USD)**

> **Note:** High-cardinality columns (e.g., Flight Number, Actual Departure Time) were dropped or used for feature extraction to avoid memory issues during one-hot encoding.

## Methodology

### Data Preprocessing & Feature Engineering

- **Data Cleaning:**  
  - Removed extra spaces from column names.
  - Handled missing values by imputing numerical columns with the median.

- **Feature Engineering:**  
  - Extracted seasonal features (month, day, hour) from the "Scheduled Departure Time" column.
  - Engineered an operational metric (Cost Efficiency = Operating Cost / Revenue).

- **Categorical Data Handling:**  
  - Dropped high-cardinality columns.
  - Applied one-hot encoding to remaining categorical features.

### Modeling

- **Baseline Model:**  
  A Linear Regression model was implemented as a baseline to evaluate the data.

- **Advanced Model:**  
  A Random Forest Regressor was trained with hyperparameter tuning using RandomizedSearchCV on a subsample of the training data. The model achieved:
  - **RMSE:** ~73.85
  - **MAE:** ~52.70
  - **R²:** ~0.99998
  
  *Note:* An extremely high R² value should be carefully evaluated for overfitting or data leakage.

### Model Explainability

- **SHAP Analysis:**  
  SHAP (SHapley Additive exPlanations) was used to interpret the Random Forest model, providing both global and local explanations for feature importance in predicting airline profitability.

## Results

The final Random Forest model achieved near-perfect performance on the test set. The SHAP analysis provided actionable insights into the key drivers of profitability, highlighting factors such as turnaround time, delay minutes, and cost efficiency.

## Usage

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/yourusername/airline-profitability-prediction.git
   cd airline-profitability-prediction
