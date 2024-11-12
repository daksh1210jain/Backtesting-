
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

Results Interpretation
Cumulative Buy-and-Hold Returns: Shows how the stock performed if held without trading.
Cumulative Strategy Returns: Shows the performance of the EMA strategy. If the cumulative returns of this strategy are higher, it indicates that the strategy has successfully outperformed buy-and-hold.
Future Improvements
Add additional technical indicators for more advanced strategies.
Implement risk management and position sizing to improve the strategy’s robustness.
Conduct further backtesting over different stocks and market conditions.
License
This project is open-source and free to use.

