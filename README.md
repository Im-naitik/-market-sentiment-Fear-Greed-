# -market-sentiment-Fear-Greed-
Analyze how market sentiment (Fear/Greed) relates to trader behavior and performance on Hyperliquid. Your goal is to uncover patterns that could inform smarter trading strategies.

# Hyperliquid Trader Behavior & Crypto Sentiment Analysis

This project analyzes historical Hyperliquid trader behavior in relation to Bitcoin market sentiment (Fear vs Greed). It computes key performance and behavioral metrics, segments traders into meaningful groups, and proposes actionable trading rules based on sentiment and trader‑type.

## Project Structure

project/
├── data/
│ ├── bitcoin_market_sentiment.csv # Daily Fear/Greed labels
│ └── hyperliquid_trader_data.csv # Per‑trade trader logs
├── notebooks/
│ └── trader_sentiment_analysis.ipynb # Main analysis notebook
├── src/
│ ├── data_prep.py # Data loading & alignment
│ ├── features.py # Feature engineering & metrics
│ ├── model.py # Next‑day PnL prediction model
│ └── dashboard.py # Streamlit dashboard script
├── outputs/
│ ├── charts/ # PNG/JPG plots
│ └── tables/ # CSV summaries
└── writeup.md # Short methodology + insights + strategy


## Requirements

- Python 3.8+
- `pandas`
- `numpy`
- `matplotlib` / `seaborn`
- `scikit‑learn`
- `streamlit` (optional, for dashboard)

You can install dependencies with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn streamlit
Data setup
Download the two datasets and place them in the data/ folder:

bitcoin_market_sentiment.csv (Fear/Greed labels by Date)

hyperliquid_trader_data.csv (trader trades with account, symbol, execution price, size, side, time, closedPnL, leverage, etc.).

Ensure the file paths in notebooks/trader_sentiment_analysis.ipynb or src/data_prep.py point to these files.

 How to run
1. Run the main analysis
Open and execute the notebook:

bash
jupyter notebook notebooks/trader_sentiment_analysis.ipynb
The notebook will:

Load and clean both datasets.

Align them by date (daily level).

Compute daily metrics (PnL, win rate, leverage, trade frequency, long/short ratio).

Segment traders (high/low leverage, frequent/infrequent, consistent/inconsistent).

Produce tables and charts showing performance and behavior differences between Fear and Greed days.

2. Run the predictive model
Execute the model script:

bash
python src/model.py
This script:

Builds features from sentiment and lagged trader behavior.

Trains a simple classifier to predict next‑day profitability buckets (Negative / Neutral / Positive).

Outputs train/test scores and feature importance.

3. Run the Streamlit dashboard
Start the lightweight dashboard:

bash
streamlit run src/dashboard.py
The dashboard allows you to:

Filter by trader segment (high‑leverage, frequent, consistent, etc.).

View daily PnL distributions by sentiment.

Inspect raw aggregated tables.

Outputs
The analysis generates:

CSV files in outputs/tables/ (e.g., segment summaries, performance by sentiment).

PNG charts in outputs/charts/ (boxplots, time‑series plots, etc.).

Example strategy rules (from findings)
Rule 1 – Leverage control on Fear days
High‑leverage traders underperform during Fear days.
→ “During Fear days, reduce max leverage for high‑leverage accounts by 20–30% of their usual cap.”

Rule 2 – Encourage activity for consistent winners on Greed days
Consistent winners maintain stable win rates and PnL even when trade frequency increases on Greed days.
→ “During Greed days, allow frequent, consistent‑winner traders to increase position size and trade frequency, but monitor drawdowns.”

Optional bonuses
Predictive model in src/model.py: next‑day PnL bucket classifier using sentiment + behavior features.

Clustering of traders into behavioral archetypes (aggressive losers, conservative winners, etc.).

Streamlit dashboard (src/dashboard.py) for interactive exploration of results.

maintained by NAITIK KATIYAR
date - feb 28 2026
