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
