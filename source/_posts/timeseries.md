---
title: Timeseries
date: 2019-07-25 14:51:27
tags:
---
---


## ARIMA-autoregreesive integrated moving average

Before we select the model, we need to test the stationarity of the data. A time series is stationary if it has constant mean and variance, and covariance is independent of time. The test I used is Dickey-Fuller test, the null hypothesis is that a unit root exists. If there is a unit root exists, then p > \alpha, we say the process is not stationary at \alpha significant level. 

In the common time series model, we have autoregressive (AR) model--AR(p), moving average (MA) model--MA(q), autoregressive–moving-average (ARMA)--ARMA(p,q) and Autoregressive integrated moving average (ARIMA)--ARIMA(p,d,q) where p,d,q stands for seasonality, trend, and noise in data.  

- AR: Auto-Regressive (p): AR terms are just lags of dependent variable. For example lets say p is 3, we will use x(t-1), x(t-2) and x(t-3) to predict x(t)
- I: Integrated (d): These are the number of non-seasonal differences. For example, in our case we take the first order difference. So we pass that variable and put d=1
- MA: Moving Averages (q): MA terms are lagged forecast errors in prediction equation.

The way I use find the suitable model is to try to look at autocorrelation and partial-autocorrelation which will give us a first idea to select the range of parameters. Then based on the AIC(Akaike information criterion) which can define the goodness of a model, to test the parameter. 

In the test, we found that the original time series is not stationary. Then we can try the first order difference and try to look at weekly data to get more smooth trend.

To find the better parameter, we can use AIC or BIC. But note that, when models are compared using these values, it is important that all models have the same orders of differencing. If a model has a order of differencing (d) of a model, then the data is changed on which the likelihood is computed, making the AIC values between models with different orders of differencing not comparable.
 
## Seasonal autoregressive integrated moving average model(SARIMA) 
SARIMA (p,d,q) * (P,D,Q,S) where (p,d,q) is same as ARIMA (These three parameters account for seasonality, trend, and noise in data), and P is the seasonal autoregressive component, D is the seasonal difference, Q is the seasonal moving average component, S is the length of the season.

The general formula for SARIMA with seasonal period as 12(months per year) is:

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space;\phi(B)\Phi(B^{12})y_t = \theta_0+\theta(B)\Theta(B^{12})\epsilon_t"/>
</p> 

where 

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; AR: \phi(B) = 1 - \phi_1B - ... - \phi_pB^p"/>
</p> 

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; MA: \theta(B) = 1 + \theta_1B + ... + \theta_qB^q"/>
</p> 

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space;Seasonal AR: \Phi(B^S) = 1 - \Phi_1B^S - ... - \Phi_PB^PS"/>
</p> 

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space;Seasonal MA: \Theta(B^S) = 1 + \Theta_1B^S + ... + \Theta_QB^QS"/>
</p> 

Since we already find there is a seasonal part in our data, then seasonal differencing will be used. The data we used later is the linear combination of the few Keywords and Heat Index between 2017/01/01 to 2019/07/13.

To compare each model with different parameter, I used log-likelihood to find out the better parameter in ARIMA. Smaller log-likelihood, AIC or BIC means this model is better.

Some comparison:

| ARIMA model | mean square error |
| ----------- | -------------- |
| ARIMA(3,0,1)(2,1,2,12) |  275 |
| ARIMA(3,1,2)(2,1,2,12) |  279 |
| ARIMA(3,0,2)(0,1,2,12) |  260 |
| ARIMA(3,0,2)(1,1,2,12) |  266 |
| ARIMA(3,0,1)(1,1,2,12) |  276 |
| ARIMA(2,0,1)(0,1,2,12) |  268 |
| ARIMA(2,1,1)(0,1,2,12) |  271 |
| ARIMA(2,1,1)(0,1,2,12) |  271 |
| ARIMA(3,1,1)(0,1,2,12) |  270 |
...

Then ARIMA(3,0,2)(0,1,2,12) may be better here.
