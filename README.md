# Introduction

The world has recently been affected by the pandemic, Covid-19 that has currently grown to more
than 3 million cases in the world. The growth rate has been exponential. Different countries have
handled the outbreak in different ways, with varying degrees of success.
A recent on-going Kaggle competition provides the data and the incentive to competitors around the
world to predict the pattern of the disease and the course taken by different countries. The aim is to
answer certain key questions regarding the disease and identifying underlying trends.
The time-series data was used in this project to model and forecast the total # of cases into the
future. The main aim was to design a model for the time-series data and forecast the number for the
future. Data was chosen was a single country, India, for this purpose. A R-Shiny dashboard was
designed and built to scale the models to all the countries. This provides the flexibility to the user to
select a country and create a model of their choice to achieve a forecast.

# Data

While the data was provided as part of the Kaggle competition, the original data source is from the
John Hopkins database. The key columns in the dataset include the following information.
- Province and Country – To identify the country, and in a few cases the province
- Date – Daily date for when the observation was recorded
- Confirmed Cases and Fatalities – Total confirmed cases and fatalities on that date

# Approach

Data was taken for India, and the preliminary plots were visualized. Data was from 30th January to
17th April and contains about 79 data points. This was converted into a time-series data object. It is
not surprising to see that there is an increasing trend in the data. Post the initial few days, the
number of cases has risen exponentially (which already suggests non-stationarity). The augmented
Dickey Fuller test results in a p-value of 0.99, and this implies non-stationarity (failed to reject H0).
By intuition, there cannot be a seasonal component as now (and hopefully will not be in the future!).
The ACF suggests slow decay, giving way to a necessity of an ARIMA component, including perhaps a
difference operator.
A differencing of the first order suggests that the mean looks relatively stable. There might be nonconstant variance but the ADF test results in a p-value of 0.01, which is satisfactory. We could
conclude that the data is relatively stationary. This makes the order d = 2.
The new dataset was created with the difference, and once again plotted to visualize the ACF and
PACF plots. These provide certain guidelines on the order of p and q, based on which a model could
be fit on the dataset.

