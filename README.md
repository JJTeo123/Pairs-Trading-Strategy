# Statistical Arbitrage: S&P 500 Pairs Trading

**S&P 500 Pairs Trading : Research Pipeline**
This repository contains the quantitative research pipeline for an S&P 500 pairs trading strategy. The workflow is broken down into modular Jupyter notebooks, covering the end-to-end process from asset screening to historical backtesting.

## Notebook Overview

### 02 · Pair Selection via Cointegration (`02_pairs_selection.ipynb`)

* **Objective:** Reduces the full S&P 500 universe down to a refined set of statistically cointegrated and economically similar pairs suitable for a mean-reversion strategy.
* **Data Cleaning:** Screens out assets with missing price or volume data and filters for I(1) integration order.
* **Similarity Filtering:** Groups potential candidate pairs by shared characteristics, such as sector, industry, market-cap, or volume buckets.
* **Statistical Screening:** Runs candidate pairs through a strict cointegration battery (including VECM rank screening and distance/correlation metrics) to finalize the trading universe.

### 03a · Baseline Walk-Forward Backtest (`03_baselineV0.ipynb`)

* **Objective:** Runs a robust, yearly equal-weight walk-forward backtest on the pairs selected in the previous stage to evaluate baseline strategy performance.
* **Methodology:** Strictly follows a walk-forward rule where the model is fitted on data from Year T-1 and traded on Year T to prevent look-ahead bias.
* **Performance Evaluation:** Tracks and compares key portfolio metrics, such as Sharpe Ratio, Annual Excess Return, and Total Trades, and drills down into the top and bottom performing individual pairs.

### 03b–05 · Baseline Walk-Forward Backtesting (`03_baselineV1.ipynb` to `05_baselineV1-P3.ipynb`)
* **Walk-Forward Evaluation:** Executes strict yearly walk-forward backtests (fitting on Year T-1, trading on Year T) to evaluate baseline OLS mean-reversion performance across different filtered pair universes (e.g., P3 Sector-Filtered).
* **Cost & Netting Engine:** Introduces `PortfolioV1` to cross opposing ticker signals intraday, accurately modeling the massive transaction cost and market impact savings of portfolio-level netting vs. gross execution.

### 06 · Strategy Rotation & Advanced Models (`06_enhancedlineV1-P3.ipynb`)
* **Dynamic Architectures:** Upgrades the pipeline to rotate through advanced statistical models, comparing the baseline static OLS against Vector Error Correction Models (VECM) and dynamically updating Kalman Filters.

### 07 · Enhanced Bayesian Optimization (`07_enhanced_bo_V1-P3.ipynb`)
* **Walk-Forward:** Introduces a rigorous rolling framework to adaptively optimize strategy parameters year-over-year.
* **Hyperparameter Tuning:** Uses Gaussian Processes equipped with strict penalty rules to find the most robust Z-score thresholds and Kalman noise parameters for each individual pair.