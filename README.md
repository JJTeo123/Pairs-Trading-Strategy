# Statistical Arbitrage: S&P 500 Pairs Trading

**S&P 500 Pairs Trading : Research Pipeline**
This repository contains the quantitative research pipeline for an S&P 500 pairs trading strategy. The workflow is broken down into modular Jupyter notebooks, covering the end-to-end process from asset screening to historical backtesting.

## Notebook Overview

### 02 · Pair Selection via Cointegration (`02_pairs_selection.ipynb`)

* **Objective:** Reduces the full S&P 500 universe down to a refined set of statistically cointegrated and economically similar pairs suitable for a mean-reversion strategy.
* **Data Cleaning:** Screens out assets with missing price or volume data and filters for I(1) integration order.
* **Similarity Filtering:** Groups potential candidate pairs by shared characteristics, such as sector, industry, market-cap, or volume buckets.
* **Statistical Screening:** Runs candidate pairs through a strict cointegration battery (including VECM rank screening and distance/correlation metrics) to finalize the trading universe.

### 03 · Baseline Walk-Forward Backtest (`03_baselineV0.ipynb`)

* **Objective:** Runs a robust, yearly equal-weight walk-forward backtest on the pairs selected in the previous stage to evaluate baseline strategy performance.
* **Methodology:** Strictly follows a walk-forward rule where the model is fitted on data from Year T-1 and traded on Year T to prevent look-ahead bias.
* **Performance Evaluation:** Tracks and compares key portfolio metrics, such as Sharpe Ratio, Annual Excess Return, and Total Trades, and drills down into the top and bottom performing individual pairs.
