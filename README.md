# Machine Learning TD — S7

This repository contains the practical lab assignments completed as part of a Machine Learning course during semester 7. It covers the fundamentals of supervised learning through five hands-on labs, from simple linear regression to neural networks and a complete end-to-end machine learning challenge.

## Labs Overview

- **LAB 1 — Linear Regression**: Simple and multiple linear regression, gradient descent, and error metrics such as MSE, RMSE and R-squared.
- **LAB 2 — Logistic Regression & KNN**: Binary and multiclass logistic regression, k-Nearest Neighbors, and evaluation metrics including confusion matrix, precision, recall and F1-score.
- **LAB 3 — Decision Tree & Random Forest**: Decision trees using Gini impurity and entropy, ensemble methods, bagging, and feature importance, applied to the Wisconsin Breast Cancer dataset.
- **LAB 4 — Multilayer Perceptron**: Neural network classification approached two ways: first with scikit-learn, then with a Keras implementation using TensorFlow.
- **LAB 5 — Machine Learning Challenge: Air Quality Prediction**: A complete pipeline on a global air pollution dataset (23,463 records). It includes data preprocessing, regression to predict the numeric AQI value (Linear Regression, Decision Tree, Random Forest), and classification to predict the AQI category (Logistic Regression, Decision Tree, Random Forest, Perceptron, MLP). Models are compared with R², RMSE, MAE, accuracy, macro-F1 and confusion matrices. Tree-based models performed best, because the AQI is the maximum of the pollutant sub-indexes and the categories follow fixed thresholds.

## Tech Stack

- Python 3
- numpy and pandas for data manipulation
- matplotlib and seaborn for visualization
- scikit-learn for classical machine learning models
- TensorFlow and Keras for the neural network implementation in Lab 4

## Notes

Large files such as datasets, CSV exports and HTML reports are excluded from this repository via `.gitignore` to keep it lightweight. Each lab folder includes the assignment instructions and the corresponding Jupyter notebook.
