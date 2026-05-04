# 📈 Sales Forecasting System
### Machine Learning-Powered Demand Prediction for Business Planning

---

## 📌 Project Overview

This project builds an end-to-end **Sales Forecasting System** using historical retail transaction data from the Superstore dataset. The goal is to predict future daily sales using machine learning, and present those predictions in a way that is immediately useful to business stakeholders — store owners, operations managers, and startup founders.

Sales forecasting is one of the most impactful applications of machine learning in real business. This system helps organizations:

- 📦 **Plan inventory** → never run out of stock or drown in unsold goods
- 💵 **Manage cash flow** → know what's coming in before it arrives
- 👥 **Prepare staffing** → put the right people in the right place at the right time
- 📉 **Reduce losses** → stop guessing, start deciding with data

---

## 🎯 Objective

> Predict **future sales** based on historical patterns and deliver business-ready visual insights.

Rather than focusing purely on model accuracy, this project emphasizes how to transform raw transaction data into **actionable forecasts** that non-technical stakeholders can understand and act on.

---

## 🗂️ Dataset

| Property | Details |
|---|---|
| **Source** | Superstore Sales Dataset (Kaggle) |
| **Records** | ~10,000 transactions |
| **Date Range** | 2020 – 2023 (4 years) |
| **Key Column** | `Sales`, `Order Date` |
| **Granularity** | Daily aggregated sales |

**Dataset Link:** [Superstore Dataset on Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final)

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.x | Core programming language |
| Pandas | Data manipulation & time-series aggregation |
| NumPy | Numerical computations |
| Scikit-learn | Linear Regression model + evaluation |
| Matplotlib | Visualizations & charts |
| Jupyter Notebook | Interactive development environment |

---

## 🔬 Methodology

### Step 1 — Data Loading & Cleaning
- 🧹 Loaded CSV with `latin1` encoding — tames those pesky special characters in retail data
- 🗓️ Parsed `Order Date` as datetime and sorted chronologically — time travel, but responsible
- 🩹 Forward-filled missing values to keep the time-series clean and unbroken

### Step 2 — Time Series Aggregation
- 🔗 Grouped raw transactions by date → daily total sales
- 📡 Resulting series picks up the natural heartbeat of the business

### Step 3 — Feature Engineering
Four time-based features extracted from each date:

| Feature | Description | Business Relevance |
|---|---|---|
| `year` | Calendar year | Captures long-term growth trend |
| `month` | Month (1–12) | Captures seasonality (holiday peaks, slow seasons) |
| `day` | Day of month | Captures end-of-month purchasing spikes |
| `day_of_week` | Day 0=Mon…6=Sun | Captures weekly buying patterns |

### Step 4 — Model Training (Linear Regression)
- 🤖 **Algorithm:** Scikit-learn `LinearRegression` — simple, fast, interpretable
- ✂️ **Split:** 80% training / 20% test — **no shuffle** because time doesn't go backwards
- 🧠 Trained on 2020–2023 data to absorb seasonal and trend patterns

### Step 5 — Evaluation
| Metric | Value | Meaning |
|---|---|---|
| **Mean Absolute Error (MAE)** | **$106.05** | Average daily prediction error |

An MAE of ~$106 on daily sales ranging from $200–$800 represents approximately **15–20% relative error** — a reasonable baseline for a linear model without advanced feature engineering.

### Step 6 — 30-Day Future Forecast
- 🔭 Generated future dates starting from the last known data point
- ⚙️ Extracted the same time-based features — same recipe, new ingredients
- 📅 Delivered day-by-day sales predictions for the next 30 days

---

## 📊 Results & Visualizations

### Chart 1 — Sales Trend Over Time
A line plot showing daily sales from 2020 to 2023, overlaid with a monthly average trend line. The output clearly shows consistent year-over-year growth, with the business scaling steadily over the 4-year period despite day-to-day volatility.

### Chart 2 — Monthly Sales Seasonality
A bar chart comparing average daily sales across all 12 months. The output highlights Q4 (Oct–Dec) as the strongest sales period driven by holiday demand, while Q1 (Jan–Feb) shows a predictable post-holiday dip — giving businesses a clear seasonal calendar to plan around.

### Chart 3 — Actual vs Predicted Sales (Test Set)
A dual-line chart comparing real sales against model predictions on the unseen test set. The output demonstrates that the model reliably tracks the overall business trend, with a Mean Absolute Error (MAE) of **$106.05** — meaning predictions are off by roughly $106 per day on average.

### Chart 4 — 30-Day Sales Forecast
A forward-looking chart showing predicted daily sales for the next 30 days, with a shaded confidence band (±12%). The output gives planners a concrete expected revenue range to inform inventory, staffing, and cash flow decisions for the coming month.

---

## 🗓️ Sample Output — Future Predictions

| Date | Predicted Sales ($) |
|---|---|
| 2024-01-01 | 735.29 |
| 2024-01-02 | 741.69 |
| 2024-01-03 | 748.09 |
| 2024-01-04 | 754.48 |
| 2024-01-05 | 760.88 |
| 2024-01-06 | 767.28 |
| 2024-01-07 | 773.67 |
| 2024-01-08 | 738.90 |
| 2024-01-09 | 745.30 |
| 2024-01-10 | 751.70 |

---

## 💼 Business Application

### How a Store Owner Can Use This Forecast

| Decision | How to Use the Forecast |
|---|---|
| **Inventory Ordering** | Order stock proportional to forecasted demand. Don't over-order in low-forecast weeks. |
| **Staffing Schedules** | Schedule more staff for high-forecast periods (weekends, Q4). Reduce casual hours in Q1. |
| **Cash Flow Planning** | Expect $735–$775/day in January. Plan vendor payments accordingly. |
| **Promotions Timing** | Run discounts in low-forecast months (Feb, Mar) to lift demand artificially. |
| **Budget Forecasting** | Use monthly totals (avg × days) as the revenue baseline for monthly P&L. |

### Example Business Insight
> *"Based on the model, expect approximately **$22,000–$23,000 in sales this month**. Plan to restock 15–20% more inventory heading into February's slump, and prepare for a 30% demand spike beginning October."*

---

## 📁 Project Structure

```
SalesForecasting/
│
├── SalesForecasting.ipynb      # Main Jupyter Notebook
├── Superstore.csv              # Dataset (download from Kaggle)
├── README.md                   # This file
│
└── charts/
    ├── 1_sales_trend.png       # Historical sales trend
    ├── 2_seasonality.png       # Monthly seasonality chart
    ├── 3_actual_vs_predicted.png  # Model validation chart
    └── 4_future_forecast.png   # 30-day forecast chart
```

---

## 🚀 How to Run

```bash
# 1. Clone or download this project
git clone https://github.com/yourusername/SalesForecasting.git

# 2. Install dependencies
pip install pandas numpy scikit-learn matplotlib

# 3. Download the Superstore dataset from Kaggle
# Place Superstore.csv in the project root

# 4. Launch Jupyter Notebook
jupyter notebook SalesForecasting.ipynb

# 5. Run all cells (Cell → Run All)
```

---

## 🔮 Future Improvements

- [ ] 🌀 **SARIMA / Prophet model** — teach the model to truly *feel* the seasons
- [ ] 🗂️ **Category-level forecasting** — separate predictions per product line, not just totals
- [ ] 📏 **Confidence intervals** — show not just the prediction, but how sure we are
- [ ] 🖥️ **Interactive dashboard** — Power BI or Plotly Dash so anyone can explore live
- [ ] 🚨 **Anomaly detection** — auto-flag days where sales go suspiciously off-script

---

## 👤 Author

**Parakala Lakshmi Hariti**  
Future Interns Program — Sales Forecasting Project  
🔗 [LinkedIn](https://www.linkedin.com/company/future-interns/)
