# Sales Forecasting (ARIMA/Exponential Smoothing)

## Problem Statement
Predicting future sales is crucial for a company to manage inventory, calculate revenue, and plan investments. Accurate sales forecasting helps a company avoid financial losses by understanding seasonal variations in sales. This is especially critical for large companies like Walmart. Predicting sales can positively impact stock prices and investor perceptions by meeting predetermined targets. Conversely, failing to meet targets can damage stock prices significantly.

## 1. Data Pre-processing
- **Data Merging**: Merged three dataframes from Walmart sales data.
- **Pivot Table Creation**: 
  - Corrected erroneous values (e.g., zero and negative values for weekly sales, as sales amounts cannot be negative).
  - Observed that average weekly sales for holidays are significantly higher than for non-holiday periods. In the training data, there are 133 weeks of non-holiday data and 10 weeks of holiday data.
  - Calculated average weekly sales for major holidays such as Super Bowl, Christmas, Thanksgiving, and Labor Day.

## 2. Data Analysis
- **Sales by Store Types and Festivals**:
  - Plotted weekly sales with respect to store types and festival types. Noted that Store A has maximum weekly sales during Thanksgiving, and all stores have minimum sales during Christmas.
  - Sales are related to the size of the stores.
  - Store 20 has the highest sales, followed by Stores 4 and 14.
- **Top Sales Periods**:
  - The top 5 weekly sales averages occur 1-2 weeks before Christmas, during Thanksgiving, Black Friday, and the end of May when schools close.
- **Correlation with Other Factors**:
  - Analyzed CPI, temperature, unemployment rate, and fuel prices against weekly sales. Found no significant patterns between these factors and weekly sales.

## 3. Models Used
### A) Random Forest
- **WMAE Score**: Weighted Mean Absolute Error (WMAE) score was calculated for the Random Forest model.

### B) Time Series Models
- **Indexing**: Time was set as the index of the dataframe.
- **Stationarity Analysis**:
  - Plotted data by weekly and monthly intervals, finding the series to be non-stationary due to trends, changing variance, and seasonal effects.
  - Stationarity is important as many time series models, including ARIMA, assume the series is stationary.
  - To achieve stationarity, common transformations include:
    - Differencing
    - Log Transformation
    - De-trending
    - De-seasonalization
  - **Transformation Methods**: Tried differencing, shifting, and log transformation. Differencing worked best among these.

### C) Holt-Winters Exponential Smoothing
- **Description**: An extension of Simple Exponential Smoothing that supports trends and seasonality in time series data. Particularly useful for forecasting data with both trends and seasonal patterns.
