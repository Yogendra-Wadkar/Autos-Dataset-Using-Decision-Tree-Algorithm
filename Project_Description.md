# Autos Dataset Price Prediction Project

## Overview

Welcome to the Autos Dataset Price Prediction project! This initiative employs machine learning to predict auto prices, utilizing a comprehensive pipeline for data analysis, feature engineering, model training, and evaluation.

## Project Pipeline

### Step 1: Problem Statement

The primary goal is to predict auto prices, employing machine learning algorithms. Price prediction involves using sophisticated algorithms to analyze automotive products and services, providing valuable insights into their market values.

### Step 2: Data Gathering

The dataset is collected from Kaggle in CSV format, forming the foundational data for subsequent analysis and model training.

### Step 3: EDA (Exploratory Data Analysis)

- Checked dataset shape: (205, 26)
- Utilized `df.info()` and `df.describe()` for comprehensive data insights.
- Addressed null values and outliers using appropriate visualizations.
- Replaced null values with column means to ensure data completeness.
- Applied feature engineering techniques, including outlier checks and column conversions.

### Step 4: Feature Engineering

Feature engineering is pivotal for shaping the dataset for optimal model performance. This step involves:

#### Outlier Handling

Identified and addressed outliers using the Interquartile Range (IQR) method. Outliers were meticulously examined and replaced to ensure robust model training.

#### Textual to Numerical Conversion

Textual data in relevant columns was converted to numerical format using the LabelEncoder(). This transformation ensures that machine learning models can effectively interpret and utilize these features.

#### Object Column Conversion

Columns containing object data types were converted to either integers or floats using the astype() function. This step is essential for compatibility with machine learning algorithms, which often require numerical inputs.

#### Custom Mapping for "num-of-cylinders" Column

The "num-of-cylinders" column required special attention. A custom mapping dictionary was defined, converting textual representations (e.g., 'four', 'six') to numerical values. The mapping was applied, and the column was converted to the int32 data type.

#### Column Removal for Model Efficiency

To enhance model efficiency and simplicity, certain columns deemed less impactful for predictive modeling were dropped. This step contributes to a streamlined dataset, focusing on essential features for accurate price prediction.

These comprehensive feature engineering steps ensure that the dataset is finely tuned, addressing outliers, transforming textual data, and optimizing feature selection for subsequent model training and evaluation.

### Step 5: Feature Selection

Checked for Assumption 1: Linearity and Assumption 2: No multicollinearity. Implemented the train-test split for the model.

### Step 6: Model Training

- Applied Linear Regression on the dataset.
- Assessed Assumption 3: Normality of residuals using `kdeplot` and Hypothesis Testing.
- Checked Assumption 4: Homoscedasticity using scatterplots.

### Step 7: Model Evaluation

- Initially achieved 100% accuracy on training data with Linear Regression, indicating overfitting.
- Trained the model using DecisionTreeRegressor, obtaining overfitting as well.
- Applied Hyperparameter Tuning, resulting in 98% accuracy on training data and 94% accuracy on testing data.

### Step 8: User-Defined Function

A user-defined function is created using a pickle file, facilitating seamless predictions with custom data. The function is designed to be easily accessible and applicable for users to make predictions based on the trained model.

```python
with open('Autos.pkl', 'wb') as f:
    pickle.dump(hyper_model, f)

class Prediction():
    def Autos_data(self, testing_data):
        with open("Autos.pkl", "rb") as f:
            model = pickle.load(f)
            prediction = model.predict(testing_data)
            print("Prediction =", prediction)
        return prediction

predict = Prediction()
testing_data = x.head(10)
predict.Autos_data(testing_data)
