<h1 align="center">Examining Beijing Air Pollution with Meteorological Variables</h1>
<p align="center"><strong>Modeling air pollution using meteorological predictors </strong>

<h2>About</h2>

This was the final project assigned in STAT 425: Applied Regression and Design during the Summer 2021 session.

The data set was assigned and distributed by the instructor, Professor Lelys Bravo De Guenni, and it was a modified version of the Beijing PM2.5 Data obtained from the University of California Irvine Machine Learning Repository. The data set can be found at:

- [https://archive.ics.uci.edu/ml/datasets/Beijing+PM2.5+Data](https://archive.ics.uci.edu/ml/datasets/Beijing+PM2.5+Data)

It consists of hourly readings of meteorological variables and the concentration of fine particulate matter with aerodynamic diameters of less than 2.5 micrometers, which is abbreviated as PM2.5, starting from January 1, 2010 to December 31, 2014.

The data analysis was completed using R within RStudio involving the use of the following packages:

- ggthemes
- gridExtra
- knitr
- lmtest
- MASS
- tidyverse

TeX was used for formatting the resulting report.

<h2>Objective</h2>

The objective was to predict the pollution of PM2.5, with the metric of concentration measured as micrograms per cubic meter, using meteorological variables like temperature and pressue, as well as temporal variables like the date and hour the observation was recorded. 

This involved finding the optimal statistical model using a variety of the methods listed below.

<h2>Methods</h2>

The analysis involved the use of the following:

- Multiple linear regression
- Residual diagnostics
- Logarithmic variable transformation
- Variable selection
- Holdout model evaluation

<h2>Results</h2>

Based on the final model, I concluded that the Beijing PM2.5 concentration was expected to increase the most as a given day's average dew point increased, as well as when both of a day's maximum wind speed in the southeastern direction and the day's maximum wind speed increased.

On the other hand, the Beijing PM2.5 concentration was expected to decrease the most as a given day's maximum combined wind speed in the northwestern direction increased, as well as when a given day's maximum combined window speed in the northwestern direction increased.

More specifically, this model is represented as

$$\displaylines{ \log(y_{\text{Avg. Daily PM2.5}}) = \beta_0 + \beta_1x_\text{Avg. Dew Point}+ \beta_2x_\text{Avg. Day Temp} + \beta_3x_\text{Avg. Day Pressure} + \\\ + \beta_4 d_\text{Max Day CBWD, NE}+\beta_5 d_\text{Max Day CBWD, NW} + \beta_6 d_\text{Max Day CBWD, SE} +\\\  + \beta_7 \log(x_\text{Max Day Wind Spd})+\beta_8\log(x_\text{Max Day Rain})+ \beta_9\log(x_\text{Max Day Snow}) + \\ + \beta_{10} x_\text{Max Day Wind Spd}+ \\\ +\beta_{11}\left( x_\text{Max Day Wind Spd}, d_\text{Max Day CBWD, NE}\right) + \\ + \beta_{12} \left(x_\text{Max Day Wind Spd}, d_\text{Max Day CBWD, NW}\right)+ \beta_{13}\left(x_\text{Max Day Wind Spd}, d_\text{Max Day CBWD, SE}\right)}$$

- $y_{\text{Avg. Daily PM2.5}}$ is the daily average PM2.5 concentration in micrograms per cubic meter
- $x_\text{Avg. Dew Point}$ is the daily average dew point
- $x_\text{Avg. Day Temp}$ is the daily average temperature
- $x_\text{Avg. Day Pressure}$ is the daily average pressure
- $d_\text{Max Day CBWD, NE}$ is the daily maximum combined wind speed in the northeastern direction
- $d_\text{Max Day CBWD, NW}$ is the daily maximum combined wind speed in the northwestern direction
- $d_\text{Max Day CBWD, SE}$ is the daily maximum combined wind speed in the southeastern direction
- $x_\text{Max Day Wind Spd}$ is the daily maximum wind speed in meters per second


The coefficients are:

| $\beta_i$    | Value    |
|--------------|----------|
| $\beta_0$    | 36.261   |
| $\beta_1$    | 0.0643   |
| $\beta_2$    | -0.0998  |
| $\beta_3$    | -0.0294  |
| $\beta_4$    | -0.335   |
| $\beta_5$    | -0.246   |
| $\beta_6$    | -0.141   |
| $\beta_7$    | -0.207   |
| $\beta_8$    | -0.208   |
| $\beta_9$    | -0.160   |
| $\beta_{10}$ | -0.00527 |
| $\beta_{11}$ | 0.00425  |
| $\beta_{12}$ | 0.00446  |
| $\beta_{13}$ | 0.0109   |

In terms of the goodness of fit of the model, the RMSE was 18.519, meaning that on average, for any given day, the predicted PM2.5 concentration would be 18.519 micrograms / cubic meter away from the day's actual observed PM2.5 concentration.

<h2>Installation</h2>

1. Download this project as zip and extract it
2. Import it in RStudio

<h2>Credits</h2>

Report formatting:

- Based on [Burak Ogan Mancarci's (University of British Columbia)](https://oganm.com/) [thesis proposal](https://github.com/oganm/ThesisProposal)
