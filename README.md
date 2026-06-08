# Retail Demand Forecasting

A LightGBM-based demand forecasting system trained on 5 years of historical sales data across multiple stores and items — predicting the next 3 months of daily sales with low MAE and RMSE.

---

## Overview

Stockouts and overstock both cost money. This project builds a forecasting pipeline that learns from historical sales patterns — seasonality, store-level variation, item-level trends — and predicts future demand at the store-item level.

Built to be practical: outputs can directly feed into inventory planning systems.

---

## Results

| Metric | Score |
|---|---|
| MAE | 847.32 |
| RMSE | 1203.18 |

Evaluated on a held-out test set spanning the final 3 months of the dataset.

---

## Pipeline

```
Raw Sales Data (5 years, store × item × day)
        │
        ▼
   Exploratory Data Analysis
   (trends, seasonality, store/item patterns)
        │
        ▼
   Feature Engineering
   (date features, lag features, rolling averages)
        │
        ▼
   LightGBM Model
        │
        ▼
   3-Month Demand Forecast
   (store × item level)
```

---

## Stack

| Component | Tool |
|---|---|
| Model | LightGBM |
| Feature engineering | Pandas, NumPy |
| Evaluation | Scikit-learn (MAE, RMSE) |
| Visualization | Matplotlib, Seaborn |

---

## Features Used

- **Date features** — day of week, month, week of year, is_weekend
- **Lag features** — sales from t-7, t-14, t-30
- **Rolling averages** — 7-day, 30-day rolling mean and std
- **Store/item encodings** — store ID, item ID as categorical features

---

## Key Findings

- Sales show clear seasonal patterns — peaks in July, dips in early Q1
- Store-level performance varies significantly across locations
- A small subset of items drives a disproportionate share of total sales
- Lag features at t-7 and t-30 are the strongest predictors

---

## Setup

```bash
git clone https://github.com/arnav-144p/retail-demand-forecasting
cd retail-demand-forecasting
pip install -r requirements.txt
```

---

---

## Author

**Arnav** — [@https_arnav](https://x.com/https_arnav) · [GitHub](https://github.com/arnav-144p) · [Portfolio](https://portfolio-arnav-two.vercel.app)
