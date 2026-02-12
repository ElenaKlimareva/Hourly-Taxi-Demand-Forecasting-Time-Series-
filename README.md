# Hourly Taxi Demand Forecasting (Time Series)

## Project Overview

**Client**: Taxi company  

This project focuses on forecasting hourly taxi demand at airports using historical order data.  
The solution combines exploratory time series analysis, feature engineering, and machine learning to build an accurate predictive model for operational decision-making.

## Objective

- **Task type**: Time series regression  
- **Target variable**: `num_orders` (number of taxi orders per hour)  
- **Evaluation metric**: Root Mean Squared Error (RMSE), with a required threshold ≤ 48 on the test set  

The goal is to predict the number of taxi orders for the next hour in order to optimise driver allocation during peak demand periods.


## Data Description

The repository contains raw data provided by the client in their original format.  
No manual modifications were made outside the preprocessing pipeline implemented in the notebooks.

The data:

- Historical taxi order records
- Time-indexed observations
- Target variable: hourly number of orders (`num_orders`)
- No missing values in the original dataset
- Resampled to hourly frequency during preprocessing


## How to Run

The project is implemented as a Jupyter Notebook.

To explore the analysis and results:

1. Clone the repository  
2. Install the required dependencies  
3. Open and run the notebook located in the `notebooks/` directory  

The notebook contains the full workflow:
- Data preprocessing
- Exploratory analysis
- Feature engineering
- Model training and validation
- Baseline comparison


## Methodology

1. **Data preprocessing**
   - Hourly resampling
   - Time index validation

2. **Exploratory time series analysis**
   - Trend analysis
   - Daily and weekly seasonality detection
   - Stationarity testing (ADF test)
   - ACF and PACF analysis

3. **Feature engineering**
   - Time-based features: `hour`, `day_of_week`
   - Lag features: `lag_1`–`lag_168`
   - Rolling statistics: `rolling_mean`

4. **Model training**
   - Linear Regression
   - Random Forest
   - KNN Regressor
   - CatBoost Regressor
   - Hyperparameter tuning with `RandomizedSearchCV`
   - Time-series cross-validation (`TimeSeriesSplit`)

5. **Baseline comparison**
   - Naïve forecast using `lag_1`
   - Daily heuristic (`lag_24`)
   - Weekly heuristic (`lag_168`)


## Results

- Best model: **CatBoostRegressor**
- Final test RMSE: **38.28**
- Required threshold: **≤ 48**
- The model significantly outperforms naïve baselines.

## Key Insights

- Taxi demand exhibits strong **daily and weekly seasonality**.
- Lag-based features substantially improve predictive performance.
- Weekly patterns (`lag_168`) are particularly strong, but the model generalises beyond simple repetition.
- The final model captures both short-term dependencies and longer seasonal cycles.


## Applications

- Driver allocation optimisation
- Peak demand management
- Operational planning
- Workforce scheduling
- Demand-aware dispatching strategies


## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib / Seaborn
- Scikit-learn
- CatBoost
- Statsmodels
- Jupyter Notebook

