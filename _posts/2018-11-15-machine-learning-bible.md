---
layout: post
title: Machine Learning notes
published: true
categories: 
- datasci
---

For newcomers to data science and machine learning (ML) like myself, the variety and the depth of different topics can be overwhelming at times. So in this post I document various notes as I learn about different facets of machiine learning. The notes are very condensed, and the intent is to use them as references in actual practice. So for total beginners this post will probably not be very helpful. Hopefully this will benefit not only myself but others out there as well. Briefly, this post contains the following:  

- [**ML workflow**](#machine-learning-workflow). From data preprocessing, missing data handling, to training and validation strategies.  
- [**ML libraries and methods**](#common-ml-libraries-and-methods). References to common methods in pandas, scikit-learn and seaborn.  
- [**Variable types**](#variable-types)  
- [**Miscellaneous notes**](#miscellaneous-notes)  

## Machine learning workflow

# Data wrangling / munging / pre-processing
1. **Data exploration.** Get a bird eye overview of the available data (how many entries? what type of values is each feature represented? ). Interpret the physical meaning of each feature (some domain knowledge will be, check data structure (i.e. what type of value is in each feature?), use visualization techniques (e.g. `box`, `scatter`, `hist` or `heatmap`) grasp univariate, bivariate or multivariate relationships. Understand the value distributions in the variable (is it normally distributed or skewed? What's the relationship between independent and dependent variables?)
2. **Missing values.** Fill in missing values by (1) dropping the columns, (2) imputing the missing values, or (3) adding new duplicate columns with imputated values filled in. There are also variations on how you decide to fill the missing values. Is it with the median, mean, mode, or some other value.
3. **Data encoding.** Encode/create dummy variables for categorical data, using one-hot encoding, or completely drop the columns.   
4. **Feature engineering.** To get the best model performance, the feature values should be normally distributed, with mean and deviation normalized. Therefore, often times some feature engineering is required to get the features into their optimal forms. 

# Training and prediction
1. **Pre-training preparations.** Split data into training, validation, and testing sets. Choose which model to best train on the data
2. **Training.** Choose a base model (or multiple ones by stacking them, e.g. random forest, deicision tree, XGBoost, etc). Train features to fit to target data 
3. **Validation.** Evaluate training results by predicting validation targets
4. **Refinement.** Iteratively improve model, avoid under/over fitting

## Common ML libraries and methods
# pandas
**Useful methods**
* `describe()`
* `dtypes`
* `get_dummies()`
* `align`
* `value_counts()`
* `groupby`
* `rename`
* `concat`, `join`, `merge`

**Univariate and bivariate plotting with pandas**
* `bar` (+stacking), `line` (+stacking), `area` (+stacking) charts and histogram
* `scatter`, `hexbin` (+stacking)

# sklearn

* .tree: `DecisionTreeRegressor`
* .linear_model: `ElasticNet`, `Lasso`, `BayesianRidge`, `LassoLarsIC`
* .kernel_ridge: `KernelRidge`
* .lightgbm (as lgb): `LGBMRegressor`
* .xgboost (as xgb): `XGBRegressor` (dominant algorithm for tabular/structured data)
* .ensemble: `RandomForestRegressor`, `GradientBoostingRegressor`
* .model_selection: `cross_val_score`, `tran_test_split`, `KFold`
* .impute: `SimpleImputer` (for missing values)
* .preprocessing: `Imputer` (for missing values), `LabelEncoder` (for categorical values), `RobustScaler`
* .ensemble.partial_dependence: `partial_dependence`, `plot_partial_dependence`
* .pipeline: `make_pipeline`

* .metrics: `mean_absolute_error`, `mean_squared_error`

* Model tuning variables: n_estimators, early_stopping_rounds, learning_rate

# seaborn
**Plotting**
* `countplot` (like `bar`), `kdeplot` (like `line`), `distplot` (like `hist`), `jointplot` (bivariate, like `scatter` and `hex`), `boxplot`, `violinplot`
* `FacetGrid`, `pairplot`
* `lmplot`
* `heatmap` (use withi .corr() on value pairs)
* pandas.plotting.parallel_coordinates

# sciply
* .stats: `probplot`

## Variable types
Most of the tabular datasets will contain values with one of the follow flavors:
* **ordinal** - positional value - ordinal scale
* **interval** - continuous, with relationships
* **categorical** - nominal scale
* **nominal** - numbers used only as a name, no intrinsic hierarchical values (inherently categorical)

## Encoding variables
1. **Find and replace:** e.g. convert "one" to "1". Create library of replacement terms, then use `.replace()`
2. **Label encoding:** first use `.astype('category')` to convert feature into categorical variables, then create a new column with the numerical mappings useing `.cat.codes`. The mapped values do not represent importance of the value, but this could mislead the algorithm into thinking one is more important than the other.
3. **One hot encoding:** use `pd.get_dummies()` to add additional columns with binary values reflecting each possible choice in the feature. This could result in many new columns, so be careful.
4. **Custom binary encoding:** use domain knowledge, you can group a selection of values into one since they have the same significance as far as the model is concerned.	


## Miscellaneous notes
* Perform cross-validation on **small** datasets to get higher quality model, use train-test split on **big** datasets to save time. To determine whether a dataset is big or small, you can run a cross-validation test and see if scores between experiments are close. If they are, then cross-validation probably doesn't do much. 
* Data leakage: any variable updated (or created) after the target value is realized should be excluded. Because when we use this model to make new predictions, that data won't be available to the model. Also, training and validation data should not intermix to avoid contaminating model fitting process.
* Model stacking (a.k.a. meta ensembling)

