
# EMA Crossover Strategy Backtesting
This project implements a simple yet effective Exponential Moving Average (EMA) Crossover Strategy for trading stocks. The strategy uses two EMAs of different periods (e.g., 20-day and 50-day) on the adjusted close price of a stock to identify buy and sell signals. A backtesting framework is set up to evaluate the performance of this strategy against a traditional buy-and-hold approach over a specified period.

Project Overview
Objective
To develop a trading strategy based on the crossover of two EMAs and evaluate its performance through backtesting on historical stock data. The project includes:

Calculating EMAs of varying periods.
Generating buy/sell signals based on EMA crossovers.
Calculating and comparing the cumulative returns of the strategy to a buy-and-hold approach.
Strategy Description
The EMA Crossover Strategy generates signals as follows:

Buy: When the short-term EMA (e.g., 20-day) crosses above the long-term EMA (e.g., 50-day), signaling upward momentum.
Sell: When the short-term EMA crosses below the long-term EMA, signaling downward momentum.
Positions are held until the opposite crossover occurs.

Key Features
Historical Data Download: Automatically downloads historical price data for the selected stock from Yahoo Finance.
Buy and Sell Signal Generation: Identifies buy and sell points based on EMA crossovers.
Performance Metrics: Calculates daily and cumulative returns for both buy-and-hold and strategy-based trades.
Visualization: Plots cumulative returns of the EMA strategy versus buy-and-hold returns for easy comparison.
Getting Started
Prerequisites
The following Python libraries are required:

pandas - for data manipulation and analysis
numpy - for numerical calculations
yfinance - for fetching historical stock data
matplotlib - for plotting results
Install them via:

bash
Copy code
pip install pandas numpy yfinance matplotlib
Usage
Define Parameters: Set your desired stock ticker and date range.
Run the Code: Execute the script to generate buy/sell signals and calculate cumulative returns.
Analyze the Results: View the cumulative returns plot to compare the strategy's performance to buy-and-hold.
Example Code
python
Copy code
import yfinance as yf
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Download historical data for the selected stock
ticker = 'MSFT'
_start = '2015-01-02'
_end = '2020-04-30'
df = yf.download(ticker, start=_start, end=_end)

# Calculate EMAs and generate signals
short_ema = 20
long_ema = 50
df['EMA_20'] = df['Adj Close'].ewm(span=short_ema, adjust=False).mean()
df['EMA_50'] = df['Adj Close'].ewm(span=long_ema, adjust=False).mean()
df['Signal'] = np.where(df['EMA_20'] > df['EMA_50'], 1, 0)
df['Position'] = df['Signal'].shift(1)
df['bnh_returns'] = np.log(df['Adj Close'] / df['Adj Close'].shift(1))
df['strategy_returns'] = df['Position'] * df['bnh_returns']
df['cumulative_bnh_returns'] = df['bnh_returns'].cumsum().apply(np.exp)
df['cumulative_strategy_returns'] = df['strategy_returns'].cumsum().apply(np.exp)

# Plot results
plt.figure(figsize=(12, 6))
plt.plot(df['cumulative_bnh_returns'], label='Buy-and-Hold Returns')
plt.plot(df['cumulative_strategy_returns'], label='EMA Strategy Returns')
plt.xlabel('Date')
plt.ylabel('Cumulative Returns')
plt.legend()
plt.show()
Results Interpretation
Cumulative Buy-and-Hold Returns: Shows how the stock performed if held without trading.
Cumulative Strategy Returns: Shows the performance of the EMA strategy. If the cumulative returns of this strategy are higher, it indicates that the strategy has successfully outperformed buy-and-hold.
Future Improvements
Add additional technical indicators for more advanced strategies.
Implement risk management and position sizing to improve the strategy’s robustness.
Conduct further backtesting over different stocks and market conditions.
License
This project is open-source and free to use.

