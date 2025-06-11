# Column-Transformer

This project demonstrates the effective use of `scikit-learn`'s `ColumnTransformer` for streamlined data preprocessing. The aim was to prepare a synthetic "covid_toy" dataset, addressing various data types and missing values, for machine learning model training.

## Project Overview

The project involved the following key steps:

### Data Loading and Initial Inspection
- The `covid_toy.csv` dataset was loaded into a pandas DataFrame.
- An initial check for null values revealed missing entries in the `fever` column.

### Data Splitting
- The dataset was divided into training and testing sets (`x_train`, `x_test`, `y_train`, `y_test`), with `has_covid` as the target variable.

### Manual Preprocessing (Demonstration)
Before introducing `ColumnTransformer`, individual preprocessing steps were performed manually to illustrate the complexity it simplifies:
- **Imputation**: `SimpleImputer` was applied to handle missing values in the `fever` column.
- **Ordinal Encoding**: `OrdinalEncoder` was used for the `cough` column, which contained ordered categorical data ('Mild', 'Strong').
- **One-Hot Encoding**: `OneHotEncoder` with `drop='first'` was applied to the `gender` and `city` columns for nominal categorical data.
- **Feature Extraction**: The `age` column was directly extracted as it required no specific transformation.
- **Concatenation**: All transformed features were manually concatenated into a single NumPy array for both training and testing datasets.

### Streamlined Preprocessing with `ColumnTransformer` (Mentos Zindagi)
The core of this project lies in demonstrating the efficiency of `ColumnTransformer`. A single `ColumnTransformer` object was configured to perform all the necessary transformations in one go:
- A `SimpleImputer` was applied to the `fever` column.
- An `OrdinalEncoder` (with defined categories `[['Mild','Strong']]`) was applied to the `cough` column.
- A `OneHotEncoder` (with `sparse_output=False` and `drop='first'`) was applied to the `gender` and `city` columns.
- The `remainder='passthrough'` argument ensured that the `age` column, which didn't require any transformation, was included in the output.

This project highlights how `ColumnTransformer` simplifies the process of applying different preprocessing steps to different columns, leading to cleaner, more maintainable, and less error-prone machine learning pipelines.
