# Stock Market Screener

A data-driven stock screener that analyzes Dow 30 stocks using technical indicators and machine learning-inspired scoring algorithms to identify promising investment opportunities.

## Overview

This project evaluates 30 major stocks from the Dow Jones Industrial Average based on multiple technical indicators and combines them into a comprehensive scoring system. The screener uses recent market data (from 2025-01-01 onwards) to calculate momentum, trend, and volume signals.

## Features

- **Multi-Factor Analysis**: Combines three complementary scoring metrics:
  - **MA50 Score**: Moving average convergence/divergence analysis using 50-day and 200-day moving averages
  - **RSI Momentum Score**: Relative Strength Index momentum detection to identify overbought/oversold conditions
  - **Volume Score**: Volume analysis combined with price trend confirmation

- **Normalized Scoring System**: All metrics are normalized between -1 and +1 for easy comparison
- **Final Composite Score**: Averaging of all three components for a holistic view
- **Visual Analytics**: 
  - Bar chart visualization of final scores by ticker
  - Color-coded heatmap for quick pattern recognition (red = negative, green = positive)

## Data Source

- **API**: Yahoo Finance (via yfinance)
- **Stocks**: Dow 30 constituents (30 large-cap US stocks)
- **Timeframe**: 1-year rolling analysis (Jan 2025 - Jan 2026)
- **Frequency**: Daily OHLCV data with auto-adjustment for splits and dividends

## Technical Stack

- **Data Analysis**: Pandas, NumPy
- **Technical Indicators**: TA-Lib (TALib)
- **Visualization**: Matplotlib, Seaborn
- **Finance Data**: yfinance

## Installation

1. Clone or download the repository
2. Create a virtual environment:
   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   ```
3. Install dependencies:
   ```bash
   pip install pandas numpy yfinance TA-Lib matplotlib seaborn
   ```

## Usage

Open the Jupyter notebook and run all cells:

```bash
jupyter notebook "Stock Market Screener.ipynb"
```

The notebook will:
1. Download historical data for all 30 Dow stocks
2. Calculate individual scoring metrics for each stock
3. Compute final composite scores
4. Generate visualizations (bar chart and heatmap)
5. Display detailed scoring results in a DataFrame

## Scoring Methodology

### MA50 Score
Combines three factors:
- **Distance from MA50** (50%): How far the current price is from its 50-day moving average
- **MA50 Slope** (30%): The direction and strength of recent moving average trend
- **Trend Regime** (20%): Whether price is above/below the 200-day moving average

### RSI Momentum Score
Measures the rate of change of RSI:
- Normalizes recent RSI changes by rolling volatility
- Positive values = RSI strengthening (bullish momentum)
- Negative values = RSI weakening (bearish momentum)

### Volume Score
Combines volume and price action:
- **Volume Component** (50%): Current volume relative to 20-day average
- **Trend Confirmation** (50%): Whether volume increases on up or down days

## Output

The screener produces:
- **Data Table**: DataFrame with individual scores (ma50_score, rsi_score, vol_score) and final_score for each ticker
- **Bar Chart**: Final scores ranked by ticker for easy comparison
- **Heatmap**: Color-coded grid view showing all stocks and their scores at a glance

## Notes

- All scores range from -1 (bearish) to +1 (bullish)
- The final_score is the arithmetic mean of the three component scores
- Higher scores suggest better momentum and trend alignment
- This is a technical analysis tool and should not be used as sole investment advice
- Historical data is auto-adjusted for stock splits and dividends

## Future Enhancements

- Additional indicators (Bollinger Bands, MACD, Stochastic Oscillator)
- Sector-based filtering and comparison
- Customizable date ranges
- Integration with broader market indices
- Machine learning-based scoring weights
- Real-time alerts for score changes

## Author

Created as part of quantitative stock analysis research.

## License

Personal use project.
