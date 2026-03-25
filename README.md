# Used Cars Price Prediction

This project aims to predict used car prices based on various car attributes. The notebook demonstrates data preprocessing, feature engineering, and training of two different regression models: Linear Regression and Polynomial Regression.

## 1. Data Loading

You can find the dataset used for this project on Kaggle here: https://www.kaggle.com/competitions/playground-series-s5e2/data

## 2. Data Preprocessing

This section covers handling missing values and feature encoding:

*   **Missing Values:**
    *   `fuel_type`: Missing values are filled with 'Gasoline'.
    *   `accident`: Missing values are filled randomly based on the observed distribution of 'None reported' and 'At least 1 accident or damage reported'.
    *   `clean_title`: This column was dropped as the test set only contained 'Yes' values, making it uninformative.

*   **Irrelevant Columns:**
    *   The `id` column was dropped from both training and test sets.

*   **Categorical Feature Encoding:**
    *   All categorical features (`brand`, `model`, `fuel_type`, `engine`, `transmission`, `ext_col`, `int_col`, `accident`) are converted to numerical representations using `LabelEncoder`.
    *   Special handling was implemented for unseen `model` and `engine` values in the test set by replacing them with an existing common category from the training set to avoid errors during `label.transform()`.

## 3. Feature Engineering (Polynomial Features)

For the second model, polynomial features of degree 3 are generated from the preprocessed numerical features. This allows the model to capture non-linear relationships between the features and the target variable (price).

## 4. Model Training and Prediction

Two linear regression models are trained and evaluated:

*   **Model 1: Basic Linear Regression**
    *   A `LinearRegression` model is trained on the preprocessed features.
    *   Predictions are made on the test set and saved to `sub.csv`.

*   **Model 2: Polynomial Linear Regression**
    *   A `LinearRegression` model is trained on the polynomial features derived from the preprocessed data.
    *   Predictions are made on the test set and saved to `subPlnm.csv`.
