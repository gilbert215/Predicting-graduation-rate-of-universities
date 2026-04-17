# Predicting University Graduation Rates

## Overview
This project applies **multiple linear regression** and **feature selection techniques** to predict university graduation rates using institutional data. The analysis explores the relationships between various college characteristics and graduation outcomes, compares different modeling approaches, and evaluates their predictive performance.

**Key Objectives:**
- Identify the most important predictors of graduation rates
- Build and compare regression models using stepwise selection and BIC
- Evaluate model performance using MAPE, RMSE, and R²
- Predict the graduation rate for Carnegie Mellon University (CMU)

## Dataset
- **Source**: College.csv (U.S. News & World Report college data)
- **Target Variable**: `Grad.Rate` (Graduation rate in %)
- **Predictors**: Apps, Enroll, Outstate, Top10perc, Top25perc

## Methodology

### 1. Exploratory Analysis
- Computed Pearson correlation coefficients between predictors and graduation rate
- Identified moderate positive correlations with `Outstate` (0.571) and `Top25perc` (0.477)

### 2. Feature Selection
- **Forward Stepwise Regression**: Iteratively added variables based on p-value threshold (0.05)
- **Bayesian Information Criterion (BIC)**: Evaluated all possible feature combinations and selected the model with the lowest BIC

**Selected Features (both methods):**
- `Outstate` – Tuition paid by out-of-state students
- `Top25perc` – Percent of new students from top 25% of high school class

### 3. Model Building & Evaluation
Two models were developed and compared:

| Model                        | MAPE     | RMSE      | R²       |
|-----------------------------|----------|-----------|----------|
| Useful Predictors (2 vars)  | 0.1921   | 13.54     | 0.378    |
| All Predictors (5 vars)     | **0.1905** | **13.45** | **0.386** |

**Conclusion**: The model using **all five predictors** performed slightly better overall.

### 4. Prediction
- **Predicted Graduation Rate for Carnegie Mellon University**: **89.20%**
- **Actual Graduation Rate in dataset**: 74%
- The prediction error falls within the model's RMSE range, highlighting limitations in predictive accuracy for individual institutions.

## Technologies Used
- **Python**
- **pandas**, **numpy**
- **statsmodels** (for OLS regression and statistical tests)
- **scikit-learn** (for performance metrics)
- **matplotlib** (for visualization)

## Key Insights
- Out-of-state tuition and the quality of incoming students (Top 25%) are the strongest predictors of graduation rates.
- Adding more predictors slightly improves model performance, suggesting complex relationships in the data.
- Even the best model explains only ~38.6% of the variance in graduation rates, indicating other important factors exist (e.g., student support, campus resources, etc.).
- Regression models can provide useful directional insights but should be used cautiously for precise individual predictions.

## Files in Repository
- `Predicting graduation rates of universities.ipynb` – Main Jupyter Notebook
- `College.csv` – Dataset
- `README.md`

## How to Run
1. Clone the repository
2. Open the Jupyter Notebook
3. Ensure required libraries are installed:
   ```bash
   pip install pandas numpy scipy statsmodels scikit-learn matplotlib
