# Guide to Time Series Forecasting Models

This guide provides an overview of common time series forecasting models, focusing on their assumptions, data requirements, and specific use cases. This will help you choose the right forecasting model for your problem.

## 1. Autoregressive Integrated Moving Average (ARIMA)

- **Assumptions**:
  - Assumes that future values are a linear function of past values and past forecast errors.
  - Assumes stationarity (the time series should have constant mean and variance over time).
  
- **Data Preprocessing**:
  - **Scaling**: Not necessary, but differencing (to achieve stationarity) may be needed.
  - **Numeric Data**: Works only with numeric data.
  - **Null Values**: Cannot handle null values directly; imputation is needed.
  - **Stationarity**: The data must be stationary or transformed to stationary using differencing.

- **Use Case**:
  - Ideal for datasets with clear trends and seasonal patterns.
  - Best suited for short-term forecasting.
  - Can handle univariate time series well.

---

## 2. Seasonal ARIMA (SARIMA)

- **Assumptions**:
  - Like ARIMA but incorporates seasonality into the model.
  - Assumes that the time series exhibits seasonal patterns in addition to trend and noise.

- **Data Preprocessing**:
  - **Scaling**: Not necessary, but the data should be stationary.
  - **Numeric Data**: Works only with numeric data.
  - **Null Values**: Cannot handle null values directly; imputation is needed.
  - **Seasonality**: Seasonality should be clearly identifiable in the data.

- **Use Case**:
  - Suitable for time series with seasonal patterns (e.g., monthly sales data, weather data).
  - Works well with univariate data where seasonal trends are strong.

---

## 3. Exponential Smoothing (ETS)

- **Assumptions**:
  - Assumes that future values depend on weighted averages of past values, with more weight given to recent observations.
  - Assumes exponential decay of past data points.
  - Works well for data with trends and seasonality.

- **Data Preprocessing**:
  - **Scaling**: Not necessary, as ETS inherently scales data.
  - **Numeric Data**: Works only with numeric data.
  - **Null Values**: Can handle null values if the missing values are small in proportion.

- **Use Case**:
  - Suitable for time series with trend and/or seasonality.
  - Works well for both short-term and long-term forecasting.
  - Can be used for both univariate and multivariate time series (with some adjustments).

---

## 4. Vector Autoregression (VAR)

- **Assumptions**:
  - Assumes that multiple time series are interdependent and that past values of these series can be used to predict future values.
  - Assumes linear relationships between multiple time series.

- **Data Preprocessing**:
  - **Scaling**: Recommended, especially if the variables have different units or magnitudes.
  - **Numeric Data**: Works with numeric data, ideally for multiple time series.
  - **Null Values**: Cannot handle null values directly; imputation is needed.
  - **Stationarity**: Data should be stationary or transformed (e.g., using differencing).

- **Use Case**:
  - Suitable for multivariate time series forecasting where variables influence each other (e.g., stock market prediction with multiple indicators).
  - Ideal for data where relationships between variables need to be captured.

---

## 5. Long Short-Term Memory Networks (LSTM)

- **Assumptions**:
  - Assumes that time series data has long-term dependencies (i.e., the value of the series at a given time depends on previous time steps).
  - Suitable for complex, nonlinear relationships in data.

- **Data Preprocessing**:
  - **Scaling**: Highly recommended, especially with neural networks.
  - **Numeric Data**: Works only with numeric data.
  - **Null Values**: Cannot handle null values directly; imputation is needed.
  - **Stationarity**: Does not require stationarity as LSTMs can model complex non-stationary series.

- **Use Case**:
  - Best suited for complex, nonlinear time series problems with long-term dependencies.
  - Ideal for large datasets with rich temporal relationships (e.g., traffic forecasting, weather prediction).

---

## 6. Prophet

- **Assumptions**:
  - Assumes that the time series has a trend, seasonality, and holidays that can affect the forecast.
  - Uses a piecewise linear or logistic growth model.
  - Does not require the data to be stationary.

- **Data Preprocessing**:
  - **Scaling**: Not necessary, as Prophet works directly with the raw data.
  - **Numeric Data**: Works only with numeric data.
  - **Null Values**: Handles missing data by default.
  - **Seasonality**: Automatically detects daily, weekly, and yearly seasonality.

- **Use Case**:
  - Ideal for forecasting time series data with strong seasonal effects and holidays (e.g., e-commerce sales with seasonal spikes).
  - Easy to use and very flexible, suitable for a wide range of time series forecasting problems.
  - Good for users without deep statistical or machine learning knowledge.

---

## 7. XGBoost for Time Series

- **Assumptions**:
  - Assumes that relationships in the data can be captured using decision trees and that boosting can improve predictive performance.
  - Does not assume any specific relationship (nonlinear or otherwise) in the data.
  
- **Data Preprocessing**:
  - **Scaling**: Not strictly necessary, but feature engineering (e.g., lag features, rolling means) is required.
  - **Numeric Data**: Can work with numeric and categorical data.
  - **Null Values**: Can handle null values through imputation and missing value encoding.
  - **Stationarity**: Does not require stationarity.

- **Use Case**:
  - Best for univariate or multivariate forecasting problems where data has complex relationships.
  - Suitable for large datasets, and it's often used in competition-winning solutions for time series forecasting.

---

## Summary Table

| Model                    | Scaling Needed | Numeric Only | Null Handling      | Stationarity Required | Use Case                                         |
|--------------------------|----------------|--------------|--------------------|-----------------------|-------------------------------------------------|
| **ARIMA**                | No             | Yes          | No (Impute Needed) | Yes                   | Short-term, univariate time series with trends  |
| **SARIMA**               | No             | Yes          | No (Impute Needed) | Yes                   | Seasonal univariate time series forecasting    |
| **ETS**                  | No             | Yes          | Yes (Handles)      | No                    | Time series with trends and/or seasonality     |
| **VAR**                  | Yes            | Yes          | No (Impute Needed) | Yes                   | Multivariate time series forecasting           |
| **LSTM**                 | Yes            | Yes          | No (Impute Needed) | No                    | Complex, nonlinear, long-term dependency data  |
| **Prophet**              | No             | Yes          | Yes (Handles)      | No                    | Seasonal data, holidays, flexible forecasting  |
| **XGBoost**              | Optional       | Yes/No       | Yes (Handles)      | No                    | Complex relationships, large datasets          |

---

This guide should provide you with a solid understanding of the different models for time series forecasting and help you decide which one is the best for your specific problem.
