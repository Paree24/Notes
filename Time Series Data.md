# Time Series Data Analysis

* A series of data points collected in time order is known as a time 
  series. Most of business houses work on time series data to analyze 
  sales number for the next year, website traffic, count of traffic, 
  number of calls received, etc. Data of a time series can be used for 
  forecasting.
* Not every data collected with respect to time represents a time series.
* Examples are Stock Price , Passenger count in airways, temperature over time, GDP

## Components of Time Series Data

**Trend** : Trend is a general direction in which something is developing or changing

![Example](https://s3.amazonaws.com/thinkific/file_uploads/118220/images/7d7/791/f5e/1549344821475.jpg)

**Seasonality** : Another clear pattern can also be seen in the above time series, i.e., the pattern is repeating at regular time interval which is known as the seasonality.

![Example](https://s3.amazonaws.com/thinkific/file_uploads/118220/images/115/9ee/826/1549344821557.jpg)

**Difference between a time series and regression problem**

Here  you might think that as the target variable is numerical it can be  predicted using regression techniques, but a time series problem is  different from a regression problem in following ways:

- The  main difference is that a time series is time dependent. So the basic  assumption of a linear regression model that the observations are  independent doesn’t hold in this case.
- Along with an increasing  or decreasing trend, most Time Series have some form of seasonality  trends,i.e. variations specific to a particular time frame.

## Hypothesis Generation

* Hypothesis generation helps us to point out the factors which might affect our dependent variable

* Below are some of the hypotheses which I think can affect the passenger count(dependent variable for this time series problem) on the JetRail:

  * There will be an increase in the traffic as the years pass by.

  * The traffic will be high from May to October.
  * Traffic on weekdays will be more as compared to weekends/holidays.
  * Traffic during the peak hours will be high.

* We will try to validate each of these hypothesis based on the dataset.

## Tools used 

* Python
* Pandas
* Sklearn

## Pandas

to_datetime()

train.Timestamp

train.resample('H or D or M or Y')

## Models

#### i) Naive Approach

- In this forecasting technique, we assume that the next expected  point is equal to the last observed point. So we can expect a straight  horizontal line as the prediction. Lets understand it with an example  and an image:

  ![Example](https://s3.amazonaws.com/thinkific/file_uploads/118220/images/cae/fd5/157/1549364621006.jpg)

  

#### ii) Moving Average

* In this technique we will take the average of the counts for last few time periods only.

  ![Example](https://s3.amazonaws.com/thinkific/file_uploads/118220/images/1f6/be6/381/1549364621459.jpg)

#### iii) Simple Exponential Smoothing

* In this technique, we assign larger weights to more recent observations than to observations from the distant past.

* The weights decrease exponentially as observations come from further in the past, the smallest weights are associated with the oldest observations.

  ![Example](https://s3.amazonaws.com/thinkific/file_uploads/118220/images/77b/752/347/1549364622440.jpg)

  ![png](https://s3.amazonaws.com/thinkific/file_uploads/118220/images/106/6d6/3f0/1549364622667.jpg)

#### iv) Holt’s Linear Trend Model

* It is an extension of simple exponential smoothing to allow forecasting of data with a trend.
* This method takes into account the trend of the dataset. The forecast function in this method is a function of level and trend.

![png](https://s3.amazonaws.com/thinkific/file_uploads/118220/images/c97/e9c/d1a/1549364623121.jpg)

## Holt winter’s model on daily time series

- Datasets which show a similar set of pattern after fixed intervals of a time period suffer from seasonality.
- The  above mentioned models don’t take into account the seasonality of the  dataset while forecasting. Hence we need a method that takes into  account both trend and seasonality to forecast future prices.
- One  such algorithm that we can use in such a scenario is Holt’s Winter  method. The idea behind Holt’s Winter is to apply exponential smoothing  to the seasonal components in addition to level and trend.

## ARIMA Model

ARIMA stands for Auto Regression Integrated Moving Average. It is specified by three ordered parameters (p,d,q).

Here p is the order of the autoregressive model(number of time lags)

d is the degree of differencing(number of times the data have had past values subtracted)

q is the order of moving average model. We will discuss more about these parameters in next section.

The ARIMA forecasting for a stationary time series is nothing but a linear (like a linear regression) equation.

### What is a stationary time series?

There are three basic criterion for a series to be classified as stationary series :

- The mean of the time series should not be a function of time. It should be constant.

- The variance of the time series should not be a function of time.

- The covariance of the ith term and the (i+m)th term should not be a function of time.

 ## Stationarity Check

 - We use Dickey Fuller test to check the stationarity of the series.
 - The intuition behind this test is that it determines how strongly a time series is defined by a trend.
 - The null hypothesis of the test is that time series is not stationary (has some time-dependent structure).
 - The alternate hypothesis (rejecting the null hypothesis) is that the time series is stationary.

## Forecasting the time series using ARIMA

- First of all  we will fit the ARIMA model on our time series for that we have to find  the optimized values for the p,d,q parameters.
- To find  the optimized values of these parameters, we will use  ACF(Autocorrelation Function) and PACF(Partial Autocorrelation Function)  graph.
- ACF is a measure of the correlation between the TimeSeries with a lagged version of itself.
- PACF  measures the correlation between the TimeSeries with a lagged version  of itself but after eliminating the variations already explained by the  intervening comparisons.

## SARIMAX

SARIMAX model takes into account the seasonality of the time series. So we will build a SARIMAX model on the time series.

