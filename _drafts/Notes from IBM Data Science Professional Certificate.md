--- 
layout: post
title: Notes from Coursera's IBM Data Science Professional Certificate program
categories: [blog, ML]
tags: [ML, data science]
---

# Major ML techniques

* Regression/estimation - predicting continuous values (y, or the dependent variable) using X, the independent variables, which can be categorical or numerical values (supervised)
* Classification - predicting item class/category (supervised)
* Clustering - finding structure in data; summarization (unsupervised)
* Associations - grouping frequently occurring items/events
* Anomaly detection - discovering abnormal and unusual cases
* Sequence mining - predicting next events; click-stream
* Dimension reduction - (PCA) reduce size of data, i.e. feature selection (unsupervised)
* Recommendation systems - recommending items
* Density estimation - (unsupervised)
* Market basket analysis - (unsupervised)


* **AI** tries to mimick human perception (computer vision, language processing, creativity, etc)
* **ML** statistical part of AI


Feature types: numeical and categorical

ML workflow: data processing (feature extraction, encoding, etc) -> train/test split -> algorithm setup -> model fitting -> prediction -> evaluation -> model export

# Regression 

## Regression types
* Simple regression: 1 X to find 1 y, fit can be linear or nonlinear
* Multiple regression: many X to find 1 y, fit can be linear or nonlinear

### Error metrics
* Mean absolute error: It is the mean of the absolute value of the errors. This is the easiest of the metrics to understand since it’s just average error.
* Mean squared error: Mean Squared Error (MSE) is the mean of the squared error. It’s more popular than Mean absolute error because the focus is geared more towards large errors. This is due to the squared term exponentially increasing larger errors in comparison to smaller ones.
* Root mean squared error: This is the square root of the Mean Square Error.
* Relative absolute error: 
* Relative squared error
* R2: not error, but is a popular metric for accuracy of your model. It represents how close the data are to the fitted regression line. The higher the R-squared, the better the model fits your data. Best possible score is 1.0 and it can be negative (because the model can be arbitrarily worse).

Ways to estimate parameters in multiple regression (theta): 
1. ordinary least squares, good for small (>10K rows) datasets
2. optimization (e.g. gradient descent), good for large datasets

To understand the linearity of problem, visually inspect $$\alpha

from sklearn import linear_model
from sklearn.preprocessing import PolynomialFeatures
from scipy.optimize import curve_fit

LinearRegression()
PolynomialFeatures()

Non-linear functions can have elements like exponentials, logarithms, fractions, quadratic, sigmoidal/logistic, and others.

# Classification

## Classification algorithms
* Decision Trees
* Naive Bayes
* Linear Discriminant Analysis
* k-Nearest Neighbors (can also be used to predict continuous values)
* Logistic Regression
* Neural Networks
* Support Vector Machines (SVM)

## Evaluation metrics
* **Jaccard index** J = intercept(y, y_hat)/ (n_y + n_y_hat - intercept(y, y_hat)), with 1.0 as the highest accuracy
* **F1-score** (by observing confusion matrix), from precision-recall (precision = TP/(TP+FP), recall = TP/(TP+FN)), F1-score = 2 x (prc x rec)/(prc + rec). highest accuracy is 1, lowest is 0.
* **log-log loss** predicted output is a probability value [0,1]. log-loss = y x log(y_hat) + (1-y) x (log(1-y_hat)). Lower log-loss means higher accuracy.

