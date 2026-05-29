# Altitude Prediction Using Machine Learning

## Overview

This project focuses on predicting rocket altitude using sensor telemetry data collected during flight. Multiple machine learning regression models were trained and evaluated to determine which approach could most accurately estimate altitude based on available sensor readings.

The project also explores data preprocessing, feature selection, handling missing values, model evaluation, and potential issues such as data leakage.

---

## Problem Statement

Given sensor measurements such as:

* Time
* Acceleration
* Pressure
* Velocity

the objective is to predict the rocket's altitude as accurately as possible using machine learning techniques.

---

## Dataset

The dataset contains telemetry data collected during rocket flight experiments.

### Features

| Feature             | Description                       |
| ------------------- | --------------------------------- |
| Time (s)            | Time elapsed during flight        |
| Velocity (m/s)      | Rocket velocity                   |
| Acceleration (m/s²) | Rocket acceleration               |
| Pressure (kPa)      | Atmospheric pressure              |
| Altitude (m)        | Actual altitude (Target Variable) |

The dataset contained missing values across multiple columns, requiring preprocessing before model training.

---

## Data Preprocessing

### Handling Missing Values

Two approaches were explored:

1. Dropping rows containing missing values.
2. Polynomial interpolation for estimating missing sensor readings.

A key observation was that interpolation performed before train-test splitting can introduce data leakage. The project therefore also evaluates a corrected workflow where interpolation is performed only after splitting the dataset.

### Feature Selection

Correlation analysis and visualization were used to identify the most informative features.

Selected Features:

* Time
* Acceleration
* Pressure

Pressure showed the strongest relationship with altitude, while velocity contributed significantly less predictive information.

### Feature Scaling

Standardization was applied for:

* Support Vector Regression (SVR)
* K-Nearest Neighbors (KNN)

Scaling was not required for:

* Linear Regression
* Random Forest

---

## Machine Learning Models

The following regression algorithms were implemented and compared:

### Linear Regression

A simple baseline model that assumes a linear relationship between features and target values.

### Random Forest Regressor

An ensemble learning technique that combines multiple decision trees to improve prediction accuracy and reduce overfitting.

### Support Vector Regression (SVR)

A powerful regression algorithm capable of modelling non-linear relationships using kernel functions.

### K-Nearest Neighbors (KNN)

A distance-based learning algorithm that predicts values based on neighboring observations.

---

## Evaluation Metrics

Model performance was evaluated using:

* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)
* R² Score

These metrics provide insight into prediction accuracy and overall model performance.

---

## Results

| Model             | MAE   | RMSE   | R² Score |
| ----------------- | ----- | ------ | -------- |
| Linear Regression | 82.92 | 170.72 | 0.9723   |
| Random Forest     | 3.53  | 5.36   | 0.99997  |
| SVR               | 26.23 | 71.10  | 0.9952   |
| KNN               | 6.75  | 11.33  | 0.99988  |

### Best Performing Model

Random Forest achieved the highest accuracy with:

* Lowest prediction error
* Lowest RMSE
* Highest R² score

---

## Key Learnings

This project provided practical experience with:

* Data cleaning and preprocessing
* Handling missing values
* Correlation analysis
* Feature engineering
* Model selection
* Hyperparameter tuning
* Feature scaling
* Regression evaluation metrics
* Identifying and preventing data leakage

One particularly important lesson was understanding how preprocessing steps performed before train-test splitting can unintentionally leak information from the test set into the training process.

---

## Future Improvements

Potential extensions include:

* Collecting additional flight datasets
* Hyperparameter optimization using GridSearchCV
* Cross-validation for more robust evaluation
* Feature importance analysis
* Gradient Boosting and XGBoost implementation
* Real-time altitude prediction from live telemetry data

---

## Technologies Used

* Python
* NumPy
* Pandas
* Matplotlib
* Scikit-Learn

---

## Author

**Nirav Karahe**

B.Tech Computer Science and Engineering
National Institute of Technology, Tiruchirappalli
Machine Learning & Data Science Enthusiast
