# Used_Car_Price_Prediction

## Abstract

This project analyzes a large-scale used vehicle dataset originally sourced from Kaggle, which contains information from over 3 million listings. The attached dataset only contains 426880 vehicles to ensure efficient computation and model development. The analysis follows the CRISP-DM framework to systematically understand the key factors that influence used car pricing. Through data cleaning, feature engineering, and regression modeling, the project investigates how vehicle characteristics impact market value. The final model provides quantitative insights into predictive features and summarizes which attributes consumers value most when purchasing a used vehicle.

## Initial Data Understanding & Cleaning

The project began with an initial screening of the original dataset to identify:

- The role of each column (target variable or predictive feature)
- The data type of each column (numerical or categorical)
- Data integrity, evaluated through the percentage of missing and the distribution and pattern of missing data across feature
- The potential for generalization of each feature in predictive modeling
- Non-informative or low-value data points that do not contribute to predictive performance

Then actions were performed:

- Dropped columns with an unacceptable percentage of missing values (greater than 60% in this study)
- Removed rows containing invalid or low-quality data points (e.g., negative or unrealistic values in price, year, and odometer)
- Removed rows with missing values in columns where the overall missing rate was below 5% to preserve data integrity
- Dropped non-informative identifier columns (e.g., ID and VIN) that do not contribute to predictive modeling
- Replaced remaining missing categorical values with "unknown" to retain as much usable information as possible


## Deep Data Understanding & Cleaning

After the initial preprocessing stage, remaining missing values were resolved. A deeper data screening and refinement process was then conducted to reduce dimensionality and improve model stability and loss behavior.

The following analyses were performed:

- Histogram visualizations were generated for both the original target variable and the log-transformed target variable to understand and identify extreme outliers.
- Features with similar informational roles were identified to reduce redundancy.
- column with large number unqiue categorical datatype that might result in huge explansion on the column when introducing dummy was identified.

Actions were conducted:

- Dropped the raws that contains the extreme outliers.
- Merged the features with similar infomrational roles.
- Group the low-frequency data points on the column with large unique categorical datatype. The hyperparameter for grouping control was determined through basedline linear regression model.

## Modeling & Evaluation

The dataset is dominated by categorical features, which significantly increases dimensionality after one-hot encoding. Applying polynomial regression in such a high-dimensional feature space would introduce substantial computational cost while providing limited practical benefit. Therefore, the modeling stage focuses on linear regression and its regularized variants, including Ridge regression and LASSO regression, to identify the most suitable predictive solution.

Model performance was evaluated using Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and R² metrics. Among the tested models, the regression model achieving the lowest MAE on the validation dataset was selected as the final model for deployment.

## Deployment

The final deployed model is a linear regression model trained on a fully cleaned and feature-engineered dataset following the CRISP-DM framework. The model provides interpretable coefficient-based insights and quantifies the price impact of categorical vehicle attributes such as model, manufacturer, paint color, and other configuration features.







