# Sales-Forecasting-Guayas-Region

## Project Overview

This project focuses on forecasting grocery sales for stores in Ecuador using various time series and machine learning models. The goal is to compare different forecasting approaches and recommend the best model for business use.

**Key Objectives:**
- Predict future sales accurately
- Compare baseline vs hyperparameter-tuned models
- Identify the most effective forecasting approach
- Provide actionable insights for inventory and staffing optimization

---

## Business Context

Retail planners need accurate sales forecasts to:
- Optimize inventory levels
- Plan staffing schedules
- Design effective promotional strategies
- Reduce waste and improve profitability

This project addresses these needs by building and evaluating multiple forecasting models.

---

## Dataset

**Source:** Favorita Grocery Sales Forecasting (Kaggle)

**Period Analyzed:** January - March 2014

**Scope:**
- **Region:** Guayas province
- **Product Categories:** Beverages, Grocery, Cleaning
- **Features:**
  - Store and item identifiers
  - Sales data (unit_sales)
  - Promotional indicators
  - Holiday information
  - Oil prices (external economic factor)
  - Temporal features (year, month, day, day of week)

**Data Preparation:**
1. Filtered to specific region and product categories
2. Created lag variables (1-day, 7-day)
3. Generated rolling averages (7-day, 14-day)
4. Merged with holiday calendar
5. Integrated oil price data

---

## Models Implemented

### 1. **XGBoost (Gradient Boosting)**
- **Type:** Tree-based machine learning
- **Approach:** 
  - Baseline: Default parameters
  - Tuned: RandomizedSearchCV
- **Key Hyperparameters Tuned:**
  - n_estimators, learning_rate, max_depth
  - min_child_weight, subsample, colsample_bytree

### 2. **Prophet**
- **Type:** Statistical time series
- **Approach:**
  - Auto-selected best seasonality mode (additive/multiplicative)
  - Baseline: Default parameters
  - Tuned: Grid search on changepoint_prior_scale and seasonality_prior_scale
- **Features:** Weekly seasonality, trend detection

### 3. **LSTM (Long Short-Term Memory)**
- **Type:** Deep learning (Recurrent Neural Network)
- **Approach:**
  - Sequence length: 7 days
  - Baseline: Simple architecture
  - Tuned: Tested multiple architectures
- **Data Format:** 3D sequences (samples × timesteps × features)
