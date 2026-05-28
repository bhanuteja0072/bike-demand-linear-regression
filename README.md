# 🚲 Bike-Sharing Demand Forecasting

## 📌 Project Overview
This repository contains a comprehensive statistical modeling project that uses multiple linear regression to forecast bike-sharing demand. The analysis focuses on understanding how various meteorological, temporal, and seasonal factors influence rental behaviors, framed as a data-driven optimization problem.

## 🔬 Methodology
The project follows a rigorous data science pipeline:
* **Exploratory Data Analysis (EDA):** Visualizing distributions, identifying collinearity, and understanding feature relationships.
* **Feature Engineering:** Handling categorical variables and scaling numerical inputs for optimal model convergence.
* **Statistical Modeling:** Implementing Multiple Linear Regression to establish a baseline understanding of feature significance.
* **Model Validation:** Evaluating the model using standard regression metrics and residual analysis to ensure statistical assumptions are met.

## 🛠️ Technologies & Tools
* **Language:** Python
* **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`
* **Environment:** Jupyter Notebook

## 📂 Repository Structure
* `bike_demand_linear_regression.ipynb`: The core Jupyter Notebook containing all data preprocessing, EDA, model training, and evaluation.
* `requirements.txt`: List of dependencies required to run the notebook.

## 📊 Results & Performance Metrics
The linear regression model was evaluated on the test dataset to measure its predictive accuracy and goodness of fit:

| Metric | Score | Description |
| :--- | :--- | :--- |
| **R² Score** | `0.825` | Proportion of variance explained by the model |
| **Adjusted R²** | `0.820` | R² adjusted for the number of predictors |
| **RMSE** | `807.82` | Root Mean Squared Error indicating average prediction error |

## 🚀 How to Run
1. Clone the repository:
```bash
   git clone [https://github.com/bhanuteja0072/bike-demand-linear-regression.git](https://github.com/bhanuteja0072/bike-demand-linear-regression.git)

   Install the required dependencies:

Bash
   pip install -r requirements.txt
Open and run the Jupyter Notebook:

Bash
   python -m jupyter notebook bike_demand_linear_regression.ipynb