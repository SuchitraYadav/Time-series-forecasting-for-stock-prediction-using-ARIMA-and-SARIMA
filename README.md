# Time-series-forecasting-for-stock-prediction-using-ARIMA-and-SARIMA
### What is Time Series Forecasting?

Time-series forecasting is a technique that utilizes historical and current data to predict future values over a period of time or a specific point in the future. By analyzing data that we stored in the past, we can make informed decisions that can guide our business strategy and help us understand future trends.

### Getting the Data

The first step is to get the data and load it to memory. We will get our stock data from the Yahoo Finance website. Yahoo Finance is a rich resource of financial market data and tools to find compelling investments. To get the data from Yahoo Finance, we will be using yfinance library which offers a threaded and Pythonic way to download market data from Yahoo.

#### Closing Price

The closing price is the last price at which the stock is traded during the regular trading day. A stock’s closing price is the standard benchmark used by investors to track its performance over time.

### Stationary
A stationary process has the property that the mean, variance and autocorrelation structure do not change over time. Stationarity can be defined in precise mathematical terms, but for our purpose we mean a flat looking series, without trend, constant variance over time, a constant autocorrelation structure over time and no periodic fluctuations. To check whether the time series is sationary we need to check decompostion and do ADF test, KPSS test.

### Time Series Decomposition Techniques

Time series data consists of observations taken at consecutive points in time. These data can often be decomposed into multiple components to better understand the underlying patterns and trends. Time series decomposition is the process of separating a time series into its constituent components, such as trend, seasonality, and noise. In this article, we will explore various time series decomposition techniques, their types, and provide code samples for each.

Time series decomposition helps us break down a time series dataset into three main components:

Trend: The trend component represents the long-term movement in the data, representing the underlying pattern.
Seasonality: The component represents the repeating, short-term fluctuations caused by factors like seasons/cycle.
Residual (Noise): The residual component represents random variability that remains after removing the trend and seasonality.

#### Additive Model:

Additive Model are the one where the variance of data doesn’t change over different values of the time series. The systematic component is the arithmetic sum of the individual effects of the predictors.

Additive model is linear and the trend line here is a straight line and seasonality has same frequency and amplitude (height and width of the cycle respectively).

#### Multiplicative Model:

Multiplicative Model are the one where as the data increases, so does the seasonal pattern or the variance increases. Here the trend and seasonal components are multiplied and then added to the error component.

Multiplicative model is non-linear, such as quadratic or exponential and the trend is a curved line and seasonality has an increasing or decreasing frequency and amplitude over time.

### ADF Test

One way to test whether a time series is stationary is to perform an Augmented Dickey-Fuller test, which uses the null and alternative hypotheses. If the p-value from the test is less than some significance level i.e., 5%, then we can reject the null hypothesis and conclude that the time series is stationary. If it's not stationary it means that the test has failed to reject the null hypothesis.

### KPSS test
KPSS is another test for checking the stationarity of a time series. The null and alternate hypothesis for the KPSS test are opposite that of the ADF test.

Null Hypothesis: The process is trend stationary.

Alternate Hypothesis: The series has a unit root (series is not stationary).

A function is created to carry out the KPSS test on a time series.

### Differencing

Differencing is a technique to transform a non-stationary time series into a stationary one. It involves subtracting the current value of the series from the previous one, or from a lagged value. Differencing can remove trends and seasonal patterns from the data, making it more stationary.

### Interpreting ACF and PACF
The autocorrelation analysis helps in detecting hidden patterns and seasonality and in checking for randomness. The autocorrelation analysis helps to identify the AR(p) and MA(q) parameters for the ARIMA model.

#### PACF
A partial autocorrelation is a summary of the relationship between an observation in a time series with observations at prior time steps with the relationships of intervening observations removed.

#### ACF
The correlation of the time series observations is calculated with values of the same series at previous times autocorrelation.

### Autoregressive Integrated Moving Average (ARIMA)
An autoregressive integrated moving average, or ARIMA, is a statistical analysis model that uses time series data to either better understand the data set or to predict future trends. 

A statistical model is autoregressive if it predicts future values based on past values. For example, an ARIMA model might seek to predict a stock's future prices based on its past performance or forecast a company's earnings based on past periods.

An ARIMA model can be understood by outlining each of its components as follows:

1. Autoregression (AR): refers to a model that shows a changing variable that regresses on its own lagged, or prior, values.
2. Integrated (I): represents the differencing of raw observations to allow the time series to become stationary (i.e., data values are replaced by the difference between the data values and the previous values).
3. Moving average (MA):  incorporates the dependency between an observation and a residual error from a moving average model applied to lagged observations.

ARIMA Parameters

Each component in ARIMA functions as a parameter with a standard notation. For ARIMA models, a standard notation would be ARIMA with p, d, and q, where integer values substitute for the parameters to indicate the type of ARIMA model used. The parameters can be defined as:

1. p: the number of lag observations in the model, also known as the lag order.
2. d: the number of times the raw observations are differenced; also known as the degree of differencing.
3. q: the size of the moving average window, also known as the order of the moving average.

How Does ARIMA Forecasting Work?

ARIMA forecasting is achieved by plugging in time series data for the variable of interest. Statistical software will identify the appropriate number of lags or amount of differencing to be applied to the data and check for stationarity. It will then output the results, which are often interpreted similarly to that of a multiple linear regression model.

 ### Seasonal Autoregressive Integrated Moving Average (SARIMA)
 
SARIMA, which stands for Seasonal Autoregressive Integrated Moving Average, is a versatile and widely used time series forecasting model. It’s an extension of the non-seasonal ARIMA model, designed to handle data with seasonal patterns. SARIMA captures both short-term and long-term dependencies within the data, making it a robust tool for forecasting. It combines the concepts of autoregressive (AR), integrated (I), and moving average (MA) models with seasonal components.

#### The Components of SARIMA

To grasp SARIMA, let’s break down its components:

1. Seasonal Component: The “S” in SARIMA represents seasonality, which refers to repeating patterns in the data. This could be daily, monthly, yearly, or any other regular interval. Identifying and modelling the seasonal component is a key strength of SARIMA.
2. Autoregressive (AR) Component: The “AR” in SARIMA signifies the autoregressive component, which models the relationship between the current data point and its past values. It captures the data’s autocorrelation, meaning how correlated the data is with itself over time.
3. Integrated (I) Component: The “I” in SARIMA indicates differencing, which transforms non-stationary data into stationary data. Stationarity is crucial for time series modelling. The integrated component measures how many differences are required to achieve stationarity.
4. Moving Average (MA) Component: The “MA” in SARIMA represents the moving average component, which models the dependency between the current data point and past prediction errors. It helps capture short-term noise in the data.

#### Seasonal Differencing 

Before we jump into SARIMA, it’s essential to understand seasonal differencing. Seasonal differencing is the process of subtracting the time series data by a lag that equals the seasonality. This helps remove the seasonal component and makes the data stationary, allowing for more straightforward modeling. Seasonal differencing is often denoted as “D” in SARIMA.

### Evaluate the Model
Let’s evaluate the forecasted sales values by comparing them to the observed sales data using two common metrics for this evaluation: Mean Absolute Error (MAE) and Mean Squared Error (MSE).

1. MAE (Mean Absolute Error) measures the average absolute difference between the observed and forecasted values. It provides a simple and easily interpretable measure of the model’s accuracy.
2. MSE (Mean Squared Error) measures the average of the squared differences between the observed and forecasted values. MSE gives more weight to large errors and is sensitive to outliers.
3. Lower values indicate better performance.
