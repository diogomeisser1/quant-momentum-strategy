# 📈 Moving Average Crossover Strategy — Walk-Forward Optimized Backtest

This repository contains a complete end-to-end pipeline for developing, optimizing, and analyzing a **momentum-based moving average crossover trading strategy**. The project is implemented in Python using `pandas`, `NumPy`, and `yfinance`, and targets three major U.S. equity ETFs: **SPY**, **QQQ**, and **DIA**.

## 🧠 Objective

To test whether a moving average crossover strategy — dynamically optimized using Sharpe ratio in a walk-forward manner — can outperform a passive buy-and-hold approach, while maintaining reasonable trade frequency and risk-adjusted returns.

---

## 📂 Repository Structure

```text
.
├── 01_Data_Collection.ipynb         # Downloads price data and computes log returns
├── 02_Data_Exploration.ipynb        # Preliminary analysis and visualization of ETF behavior
├── 03_MA_Strategy_Baseline.ipynb    # Simple MA crossover strategy visualization (static parameters)
├── 04_Backtest_Optimization.ipynb   # Walk-forward strategy with parameter tuning via Sharpe ratio
├── 05_Results.ipynb                 # Compiles and interprets final strategy performance
├── data/                            # (Optional) Folder to store CSVs of downloaded/processed data
├── strategy_results_sharpe_based_final.csv  # Final test results for each ETF per walk-forward period
└── README.md
```

---

## 📊 Strategy Summary

The strategy buys when the short-term moving average crosses **above** the long-term moving average (plus a threshold), and sells when it crosses **below** (minus the threshold). Optimization is based on **out-of-sample Sharpe ratio**, not return, to prioritize consistency and risk-adjusted performance.

Key Features:
- ✅ Walk-forward training/testing splits (3-year train, 2-year test)
- ✅ Buffer period to avoid lookahead bias in MA computation
- ✅ Sharpe ratio optimization across:
  - Short MA window: 10–100
  - Long MA window: Short+10 to 255
  - Threshold: 0.00000 to 0.00475 (in 0.00025 steps)
- ✅ Minimum trade filter to avoid overfitting

---

## 📌 Results Snapshot

Each row in the final CSV includes:
- ETF (SPY, QQQ, DIA)
- Train/Test period range
- Optimized short/long MA + threshold
- Out-of-sample strategy return
- Trade count
- Sharpe ratio

> 📝 **Note:** Strategy returns and Sharpe ratios are modest, as expected for a conservative moving average system, but show consistent outperformance for DIA in particular.

---

## 📘 How to Run Locally

1. Clone the repo:
```bash
git clone https://github.com/yourusername/moving-average-strategy.git
cd moving-average-strategy
```

2. (Optional) Create virtual environment and install dependencies:
```bash
pip install -r requirements.txt
```

3. Run notebooks in order:
   - `01_Data_Collection.ipynb`
   - `02_Data_Exploration.ipynb`
   - `03_MA_Strategy_Baseline.ipynb`
   - `04_Backtest_Optimization.ipynb`
   - `05_Results.ipynb`

---

## 🚧 Known Limitations

- No transaction cost or slippage modeled (future enhancement)
- Fixed trade sizing (equal weight); no volatility scaling or dynamic position sizing
- Results use log returns; drawdown metrics and rolling Sharpe coming soon

---

## 📈 Future Plans

- Add slippage/fee sensitivity testing
- Compare against RSI and Bollinger Band strategies
- Incorporate rolling Sharpe and drawdown visualizations
- Package strategy into a reusable Python module
- Explore live paper trading via Alpaca or IBKR

---

## 👨‍💻 Author

**Diogo Meisser**  
Master's in Economics, Texas A&M University  
📧 diogomeisser@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/diogom2)
