# Demand Forecasting & Planning Workbook (SAP IBP style)

A demand planning workbook built on 5 years of retail sales data,
modelled on how statistical forecasting and planning views work in
SAP Integrated Business Planning.

## Data
Store Item Demand Forecasting Challenge (Kaggle) — 5 years of daily
sales, 50 items, 10 stores. This project uses Store 1, aggregated
from daily to monthly buckets (60 periods, 2013–2017).

## Method
Models were trained on 2013–2016 (periods 1–48) and tested on 2017
(periods 49–60), which was held out entirely.

- **Naive (seasonal)** — same month last year
- **Holt-Winters (FORECAST.ETS)** — level, trend and 12-month seasonality
- Accuracy measured with **MAPE**; direction of error measured with **bias**

## Results

| Approach | Average MAPE (2017) |
|---|---|
| Naive for all items | _4.30_% |
| Holt-Winters for all items | _4.29_% |
| Best-fit model per item | _3.99_% |

Naive was the better model for **33** items and Holt-Winters for **17**.
No single model was best across the range, which is why per-item model
selection matters.

## Planning View
The Planning View sheet reproduces an IBP-style planning screen:
time buckets across the top, key figures down the side.

- **Actuals**, **Statistical Forecast** — calculated
- **Manual Adjustment** — editable (yellow), where a planner enters
  judgement such as a promotion uplift
- **Consensus Demand** — statistical forecast plus adjustment
- **Error %** — with a conditional-format alert above 20%

## IBP concepts applied
Planning level (product × location) · time buckets · key figures ·
statistical vs consensus forecast · best-fit model selection ·
forecast error (MAPE) and bias · alerts

## Files
- `Demand_Forecasting.xlsx` — the full workbook
- `planning-view.png`, `actual-vs-forecast.png`, `results.png`, `mape-comparison.png`
