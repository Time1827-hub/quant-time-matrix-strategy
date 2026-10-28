# Quantitative Time-Series Discretization Strategy

## Overview
This repository contains an alternative quantitative trading model for energy commodities (Brent Crude / WTI). The strategy is based on calendar time-discretization and volatility clustering, rather than traditional lagging price indicators.

## Strategy Logic
1. **Time Matrix Core:** Every calendar day is assigned a discrete state (1-9). States 1 & 8 indicate expansion phases (Long), while 5, 7 & 9 indicate compression/chaos phases (Short).
2. **Signal Clustering ("Wall" filter):** Trades are only executed if at least 2 signals from the same group appear within a 3-day window. This eliminates market noise.
3. **Momentum Filter:** No trades against the 3-day price momentum.
4. **Early Entry:** The system enters the trade 8 days prior to the cluster formation.
5. **Risk Management:** 20% of equity per trade.

## Performance Metrics (Out-of-Sample Backtest, 2018-2023)
* **Total Return:** +67.67%
* **Market Return (Buy & Hold):** +15.73%
* **Sharpe Ratio:** 1.21
* **Sortino Ratio:** 1.62
* **Max Drawdown:** -7.38%
* **Win Rate:** 55.25%

### Crisis Alpha Profile
* **2008 Financial Crisis:** +26.6% (Market: -59%), Sharpe: 2.38
* **2020 COVID-19 Crash:** +67.6% (Market: -22%), Sharpe: 1.21

## Tech Stack
Python 3, Pandas, NumPy, Matplotlib, yfinance.
