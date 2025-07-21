# 📈 Momentum Strategy Backtesting

This project explores and evaluates a momentum-based trading strategy using **moving average (MA) crossovers** across major ETFs: **SPY**, **QQQ**, and **DIA**. We experiment with different configurations and backtesting methods to demonstrate how strategy evaluation can evolve from basic testing to robust walk-forward validation.

---

## 🔍 Project Objectives

- Implement a momentum strategy using short/long moving average crossovers
- Avoid overfitting by incorporating realistic constraints (buffer period, walk-forward validation)
- Compare performance using return, Sharpe ratio, and trade count metrics

---

## 📁 Project Structure

| Notebook | Description |
|----------|-------------|
| `01_Data_Collection.ipynb` | Pulls ETF data using `yfinance` and saves it to CSV |
| `02_Data_Exploration.ipynb` | Explores return behavior and trends of SPY, QQQ, and DIA |
| `03_MA_Strategy_Baseline.ipynb` | Implements the simplest MA crossover without threshold or buffer |
| `04_Backtest_80-20Split.ipynb` | Demonstrates overfitting by optimizing on the test set |
| `05_Backtest_WalkForward_Return.ipynb` | Walk-forward backtest optimizing MA pairs by **raw return** |
| `06_Backtest_WalkForward_Sharpe.ipynb` | ✅ **Final model**: walk-forward with buffer, trade count filter, and **Sharpe ratio optimization** |
| `07_Results.ipynb` *(optional)* | For visualizing cumulative returns, Sharpe trends, etc. (to be filled) |

---

## ✅ Final Model

The most robust version of the strategy is in:

> 📌 `06_Backtest_WalkForward_Sharpe.ipynb`

It features:
- **Walk-forward backtesting** with training and testing windows
- **Buffer period** to avoid lookahead bias
- **Trade count minimum** to filter out unreliable strategies
- Optimization based on **Sharpe ratio**, not just return

---

## 📊 Metrics Tracked

- Cumulative Return
- Sharpe Ratio
- Trade Count
- Buy & Hold Benchmark Comparison

---

## 📦 Requirements

Install dependencies using pip:

```bash
pip install pandas numpy matplotlib yfinance
