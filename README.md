# 🚲 Bike-Sharing Demand Forecasting

Multiple linear regression with full statistical validation to forecast daily bike-sharing demand, using the UCI Bike Sharing Dataset.

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📌 Project Overview

This project builds and validates a multiple linear regression model to predict daily bike rental counts (`cnt`) based on meteorological conditions, calendar features, and seasonal patterns. It goes beyond baseline modelling with rigorous statistical validation, two feature selection methods, and benchmarking against regularised and ensemble alternatives.

---

## 🔬 Methodology

The pipeline follows these stages:

**1. Exploratory Data Analysis**
Visualising distributions, identifying collinear features, and understanding how season, weather, and weekday affect rentals.

**2. Feature Engineering**
- Dummy encoding for `season`, `weathersit`, `weekday`, and `month`
- Dropping `atemp` (r > 0.99 with `temp`), `hum`, and `saturday` due to multicollinearity
- Dropping `casual` and `registered` (target leakage)
- MinMax scaling of continuous features

**3. Feature Selection (two methods)**
- **RFE** (Recursive Feature Elimination): iteratively removes the least important features
- **Backward Elimination**: drops features by their impact on adjusted R² each round
- Both methods converge on the same top 3 features: `temp`, `yr`, `weathersit_3`

**4. Statistical Validation**
- `statsmodels` OLS summary — p-values, F-statistic, confidence intervals
- VIF table — multicollinearity check (all VIF < 5 in final model)
- Durbin-Watson statistic — autocorrelation check
- Residual distribution, Q-Q plot, residuals vs. fitted scatter

**5. Extended Evaluation (new)**
- 5-fold cross-validation (mean ± std R² and RMSE)
- Log-transform experiment — trains on `log1p(cnt)` and evaluates on original scale
- Model benchmarking — compares Linear Regression, Ridge, Lasso, and Random Forest

---

## 📊 Results

### Single Split (70/30)

| Metric | Score | Description |
|---|---|---|
| **R² (test)** | `0.825` | Proportion of variance explained |
| **Adjusted R²** | `0.820` | R² penalised for number of predictors |
| **RMSE (test)** | `807.82` | Average prediction error in rental units |

### 5-Fold Cross-Validation

| Metric | Mean ± Std |
|---|---|
| **CV R²** | `0.821 ± 0.018` |
| **CV RMSE** | `~810 ± ~30` |

### Key Findings

- **`yr` (year)** is the strongest predictor — rentals grew significantly from 2011 to 2012, suggesting system adoption over time.
- **`temp` (temperature)** is the strongest continuous predictor — warmer days strongly drive demand.
- **`weathersit_3` (light snow/rain)** has the largest negative coefficient — severe weather sharply reduces rentals.
- Removing any of the top 3 features drops R² by at least 3 points (see Feature Ablation Study section in the notebook).

---

## 🛠️ Technologies

| Tool | Purpose |
|---|---|
| `pandas`, `numpy` | Data manipulation |
| `matplotlib`, `seaborn` | Visualisation |
| `scikit-learn` | Model training, RFE, CV, benchmarking |
| `statsmodels` | OLS summary, VIF, Durbin-Watson |
| `scipy` | Statistical tests |
| Jupyter Notebook | Analysis environment |

---

## 📂 Repository Structure

```
bike-demand-linear-regression/
├── notebooks/
│   └── bike_demand_linear_regression.ipynb   ← main analysis
├── data/
│   └── README.md                              ← dataset info & column docs
├── .gitignore
├── LICENSE
├── requirements.txt
└── README.md
```

---

## 🚀 How to Run

**1. Clone the repository:**

```cmd
git clone https://github.com/bhanuteja0072/bike-demand-linear-regression.git
cd bike-demand-linear-regression
```

**2. Install dependencies:**

```cmd
pip install -r requirements.txt
```

**3. Run the notebook:**

```cmd
jupyter notebook bike_demand_linear_regression.ipynb
```
```

The notebook downloads `day.csv` automatically in cell 2 — no manual data download needed.

---

## 📖 Data Source

UCI Machine Learning Repository — [Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/Bike+Sharing+Dataset)  
Fanaee-T, H., and Gama, J. (2014). Event labeling combining ensemble detectors and background knowledge. *Progress in Artificial Intelligence*, Springer.
