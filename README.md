# Quantitative Time-Series Discretization Strategy

## Overview
This repository contains an alternative quantitative trading model for energy commodities (Brent Crude / WTI). The strategy is based on **calendar time-discretization** and **volatility clustering**, rather than traditional lagging price indicators.

*Note: The proprietary time-matrix data (states 1-9) and core logic were developed by the author. The Python implementation and backtesting script were generated and optimized using AI assistance.*

## Strategy Logic
1. **Time Matrix Core:** Every calendar day is assigned a discrete state (1-9). States 1 & 8 indicate expansion phases (Long), while 5, 7 & 9 indicate compression/chaos phases (Short). States 2, 4 & 6 are considered market noise.
2. **Signal Clustering ("Wall" filter):** Trades are only executed if at least 2 signals from the same group appear within a 3-day window. This eliminates market noise.
3. **Momentum Filter:** No trades against the 3-day price momentum (e.g., no shorting if the price is rising).
4. **Early Entry (Proprietary Edge):** The system enters the trade **8 days prior** to the cluster formation, taking advantage of the accumulation phase before the crowd reacts.
5. **Risk Management:** 20% of equity per trade.

## Performance Metrics (Out-of-Sample Backtest, 2018-2026)
* **Total Return:** +76.70%
* **Market Return (Buy & Hold):** +66.14%
* **Max Drawdown:** -9.19%
* **Win Rate:** 53.69%
* **Sharpe Ratio:** 0.92
* **Sortino Ratio:** 1.22

### Peak Performance (2018-2023)
During the highly volatile 6-year period (including COVID-19), the strategy achieved:
* **Sharpe Ratio:** 1.21
* **Max Drawdown:** -7.38%

### Crisis Alpha Profile
The strategy is designed to act as a crisis hedge:
* **2008 Financial Crisis:** +26.6% (Market: -59%), Sharpe: 2.38
* **2020 COVID-19 Crash:** +67.6% (Market: -22%), Sharpe: 1.21
* **2014 Shale Crash:** +4.1% (Market: -46%), Sharpe: 1.17

## Tech Stack
* Python 3
* Pandas, NumPy, Matplotlib, yfinance

## Disclaimer
This code is for educational and research purposes only. It is not financial advice. Past performance does not guarantee future results. 

*Future time-matrix data (2027+) is proprietary and not included in this repository.*
