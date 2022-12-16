# Crypto-Pairs-Trading-Strategy
In this notebook, we will create a pairs trading strategy. Pairs trading is a market neutral strategy where we go long on one crypto pair and short on the other one, betting that the spread between the two would eventually converge to their mean.

# 1. Import the libraries and data
First, we will import the necessary libraries and then, fetch the Bitcoin (BTC/USD) and Frax Share (FXS/USD) data from csv files using the pandas 'read_csv' function.

# 2. Calculate the hedge ratio using the ordinary least square method.
Hedge ratio is calculated using the linear regression.
The linear equation typically takes the form:
y = βX + ϵ
where y is the dependent variable, X is the independent variables, and β is the slope that we want to estimate and ϵ is the error term.
The OLS function from the statsmodels package is used to calculate the hedge ratio.
The function takes dependent_variable(y) and independent_variable(X) as parameters.

# 3. Calculate the spread using the hedge ratio.
We calculate the spread using the hedge ratio.
Spread = independent_variable - hedge_ratio * dependent_variable

# 4. Check for cointegration using the ADF test.
We check whether the crypto pair is cointegrated or not. We use the ADF test to check the cointegration.
The test statistics is less than critical values at 90% confidence levels. So, we can reject the null hypothesis and state that the BTC/USD and FTX/USD are cointegrated with 90% confidence level from Jan 01, 2021 to Dec 16, 2022.

# 5. Calculate the Bollinger bands
Upper Band: The upper band is the 'n' standard deviations above the moving average of the price.
Middle Band: The middle band is the moving average of the price.
Lower Band: The lower band is the 'n' standard deviations below the moving average of the price.

# 6. Trading signals
Buy Signal:
If spread crosses below the lower Bollinger band then buy the spread and exit the position when it reaches to the middle band.
Sell Signal:
If spread crosses above the upper Bollinger band then sell the spread and exit the position when it reaches to the middle band.

 # 7. Calculate the strategy returns
Calcuate the daily returns of BTC
Calculate the daily returns of FXS
Calculate daily returns by subtracting daily returns of FXS from BTC
The strategy returns are generated by multiplying the previous position with the daily returns
