# California Housing Price Prediction

This project predicts California median house values using regression models. The goal was to build a complete machine learning workflow, from data exploration and feature engineering to model training, evaluation, and residual analysis.

## Project Overview

The dataset used is the California Housing dataset from `sklearn.datasets`. It contains housing and demographic information for California districts, including median income, house age, average rooms, population, occupancy, and location-based features.

The target variable is:

```
MedHouseVal
```

This represents the median house value in units of $100,000.

## Objectives

- Explore and understand the dataset
- Visualize outliers and feature distributions
- Create new useful features
- Reduce multicollinearity
- Train and compare regression models
- Evaluate model performance using regression metrics
- Use residual plots to understand model errors

## Workflow

1. Loaded the California Housing dataset
2. Explored the dataset using shape, summary statistics, and data information
3. Visualized outliers using boxplots
4. Split the data into training and testing sets
5. Created engineered features:
   - `Bedrm_Ratio`
   - `Dist_to_SF`
   - `Dist_to_LA`
6. Removed replaced or highly related columns:
   - `AveBedrms`
   - `Latitude`
   - `Longitude`
7. Scaled features for regularized models
8. Trained and compared:
   - Linear Regression
   - Ridge Regression
   - Lasso Regression
9. Evaluated model performance with MAE, RMSE, and R2
10. Used residual plots to inspect prediction errors

## Models Used

### Linear Regression

Linear Regression was used as the main baseline regression model. It assumes a linear relationship between the input features and the target variable.

### Ridge Regression

Ridge Regression was used to reduce the effect of multicollinearity and control large coefficients using L2 regularization.

### Lasso Regression

Lasso Regression was used to apply L1 regularization, which can shrink less useful feature coefficients toward zero.

## Model Performance

The models produced similar performance:

| Model | MAE | RMSE | R2 |
|---|---:|---:|---:|
| Linear Regression | 0.5625 | 0.7743 | 0.5424 |
| Ridge Regression | 0.5625 | 0.7743 | 0.5425 |
| Lasso Regression | 0.5624 | 0.7742 | 0.5426 |

The best model was Lasso Regression by a very small margin.

## Interpretation

The model explains about 54% of the variation in median house values. This shows that the features have useful predictive power, but the model does not capture all patterns in the data.

The RMSE of about `0.774` means the typical prediction error is approximately:

```
0.774 x $100,000 = $77,400
```

## Residual Analysis

A residual plot was used to compare predicted values against model errors.

The residual plot showed that many errors were centered around zero, which means the model made reasonable predictions for many observations. However, the residuals were not completely random and showed some visible structure. This suggests that linear models may not fully capture the non-linear relationships in the housing data.

## Key Insights

- Median income is an important predictor of house value.
- Feature engineering helped make location and room-related information easier to interpret.
- Ridge and Lasso did not greatly improve performance over Linear Regression.
- The residual plot suggests that a non-linear model may perform better.
- Linear models are useful for interpretability, but they may be limited for complex housing-price patterns.

## Limitations

- Linear models may not capture complex spatial patterns.
- Latitude and longitude were replaced with distance-based features for easier interpretation.
- The dataset contains non-linear relationships that simple linear models may miss.
- Outliers and capped house values can affect model performance.

## Next Steps

Future improvements could include:

- Trying Random Forest Regression
- Trying Gradient Boosting Regression
- Performing hyperparameter tuning
- Comparing models with cross-validation
- Testing different outlier-handling strategies
- Adding more advanced location-based features

## Tools and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

## Conclusion

This project demonstrates a full regression machine learning workflow for predicting California housing prices. The final models performed better than a simple baseline, but the residual analysis showed that linear models have limitations on this dataset. This makes the project a strong foundation for future improvement with non-linear machine learning models.
