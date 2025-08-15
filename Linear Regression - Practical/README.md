# Linear Regression Practical Assignment

## Overview
This repository contains using linear regression techniques for a machine learning assignment. It covers simple and multiple linear regression, comparing closed-form solutions, Stochastic Gradient Descent (SGD), and Batch Gradient Descent (BGD), with and without \( L_2 \) regularization. It includes data preprocessing, model training, and performance evaluation using `Python`.

## Key Aspects

- **Dataset**: A dataset with categorical and numerical features (e.g., `region`, `smoker`, `gender`) is used to predict a target variable.
- **Simple Linear Regression**:
  - Models trained using closed-form solution, SGD, and BGD.
  - Cost function: Mean Squared Error (MSE).
  - BGD outperforms SGD, approaching the global minimum.
  ![Cost vs. Epoch for Simple Linear Regression](./figs/costvsepoch_one_var.png)
- **Multiple Linear Regression**:
  - Preprocessing: Categorical features encoded with One Hot Encoding (`region`) and Integer Encoding (`smoker`, `gender`); data standardized to prevent gradient explosion.
  - Training: Closed-form solution uses Moore-Penrose pseudo-inverse; SGD and BGD compared for convergence.
  - \( L_2 \) regularization applied to closed-form solution, with optimal \( \lambda = 10^{-4} \).
  - Key Figures:
    - ![Test Error vs. Dataset Size for All Methods](./figs/dataset_size_compar.png)
    - ![Test Error for Different \( \lambda \) Values](./figs/diff_lambda.png)
- **Findings**:
  - BGD is more reliable than SGD for small datasets.
  - Closed-form solution stabilizes with sufficient data (~20 samples).
  - Regularization improves model stability.

## Libraries Used

The analysis was implemented in `Python` using the following libraries:

- **NumPy**: For numerical computations, matrix operations (e.g., `inv`, `pinv` for closed-form solutions).
- **Pandas**: For data manipulation and handling datasets (e.g., loading and preprocessing data).
- **Scikit-learn**: For data splitting (`train_test_split`) and standardization (`StandardScaler`) to ensure stable model training.
- **Matplotlib and Seaborn**: For creating visualizations (e.g., plots of cost function, error trends).
