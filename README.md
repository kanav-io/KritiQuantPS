KritiQuantPS => Quantitative Trading Strategy for the GB Intraday Electricity Market
=====================================================================================

Overview
--------
KritiQuantPS is a project focused on developing and backtesting a quantitative trading strategy for the Great Britain (GB) intraday electricity spot market. The strategy leverages statistical and technical analysis to capitalize on intraday price volatility, using real market data from October 1, 2024, to December 31, 2024.

Market Context
--------------
The GB electricity market is a liberalized, competitive environment where electricity is traded between generators, suppliers, and other participants. The intraday spot market allows for electricity to be bought and sold on short notice, with prices fluctuating significantly due to demand-supply dynamics, renewable energy variability, and unexpected outages.

Data Acquisition
----------------
• Spot market data was sourced from Elexon, covering multiple eight-day periods.  
• All data files were compiled and standardized into a single dataset for robust analysis and strategy evaluation.

Solution Approach
-----------------
The trading system consists of three main components:

1. Regime Identification
   • Uses Average True Range (ATR) to assess market volatility.  
   • Applies the Cumulative Sum (CUSUM) method to detect shifts in price regimes (bullish, bearish, stagnant).  
   • Incorporates time-specific demand patterns, such as increased residential demand in the evening and low demand early morning, to classify likely market regimes.

2. Trend Identification
   • Employs Bollinger Bands to identify overbought/oversold conditions and dynamic support/resistance levels.  
   • Utilizes the Zig-Zag indicator to filter out minor price movements and highlight significant trend changes.

3. Trading Strategy
   • Trades are executed only when both regime and trend indicators align.  
   • Capital allocation is dynamic:  
     o 10% of capital is allocated during confirmed bullish hours with strong signals.  
     o 5% in less definitive scenarios to limit risk.  
   • Risk management includes:  
     o Value at Risk (VaR) calculations at a 95% confidence level to determine exposure.  
     o Profit-taking by squaring off 60% of a position after a 5% gain and adjusting stop-losses.  
     o Immediate exit if losses exceed 2% on any position.

Performance Metrics
-------------------
• Sharpe Ratio (Annualized): 9.24  
• Maximum Drawdown: -7.25%  
• Annualized Volatility: 54.02%  
• Sortino Ratio: 5.26  
• 3-Month Returns: 327.42%



Statistical Validation
----------------------
• T-test Statistic: 3.86 (P-value: 0.00012, significant at 0.05 level)  
• Mean Return: 0.00132 (95% CI: [0.00063, 0.00197])  
• Win Rate: 40.90%  
• Profit Factor: 1.94  
• Profitability: Total profit (2.10) exceeds total loss (1.08)

Robustness Check
----------------
• Look-back analysis using data segmentation confirms the strategy's signals are consistent and free from lookahead bias.

References
----------
• Data and market reviews from Britain's Electricity Explained (2023, 2024)  
• Elexon data files (118 files, 8-day periods)  
• Combined and processed CSV datasets

How to Use
----------
Clone the repository:

    git clone https://github.com/kanav-io/KritiQuantPS.git
    cd KritiQuantPS

Install dependencies (refer to requirements.txt if available):

    pip install -r requirements.txt
