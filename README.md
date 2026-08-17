# Nairobi Supply Chain EDA — Ubuntu AnalytiQ Week 01

Data & AI Mastery Mentorship · 12-Week Program · Building for Us by Us

> "You cannot build solutions without first understanding the data that shapes your world."

## Project Overview

Exploratory data analysis of 12 months of daily stock movements across a Nairobi distributor network, covering 15 product categories from 10 Kenyan suppliers across 7 Nairobi regions. The goal: understand where and why stockouts happen, as groundwork for automating stockout prevention in later weeks of the program.

Stockouts of staple goods like unga, cooking oil, and milk can cost a distributor 15–25% of weekly revenue — this analysis identifies which categories, regions, and suppliers drive that risk.

## Dataset

- **Source:** `Wk 01 - Supply Chain Dataset.xlsx`
- **Size:** 4,500 rows × 12 columns
- **Period:** January 2023 – December 2024
- **Fields:** units ordered vs. received, units sold vs. stock on hand, lead times, stockout flags, region, category, supplier

## Data Quality

**Data Quality Score: 100%**

| Check | Result |
|---|---|
| Missing values | 0 across all 12 columns |
| Units_Received > Units_Ordered anomalies | 0 rows |
| Duplicate TransactionIDs | 0 |

The dataset is unusually clean — no imputation or deduplication was required. This is a caveat worth noting: real-world operational data would typically show some missingness or logging errors, suggesting this dataset may be simulated/curated rather than raw.

## Key Findings

- **Dairy is the highest stockout-risk category** — stockout rate of ~6.7%, nearly double Baby products (~4.9%) and well above Grain and Flour (~2.0–2.4%). Given dairy's short shelf life, it's the top priority for automated stockout prevention.
- **Westlands is the worst-performing region** — 28 stockout events over two years, followed by Thika Road (26) and Mombasa Road (25). Eastleigh had the fewest (20). Lead times and fulfillment rates are consistent across suppliers, pointing to a regional demand-forecasting gap rather than a supplier problem.
- **No single underperforming supplier** — average lead times cluster tightly between 11.2–11.8 days, and fulfillment rates sit around 92–93% across the board. Stockouts appear driven more by demand spikes and regional stocking gaps than supplier reliability.

**Overall metrics:** 3.7% stockout rate · 11.5 day avg lead time · 92.6% avg fulfillment rate

## What the Data Can't Answer

Why did stockouts spike sharply in certain months (e.g. 13 events around mid-2023)? The dataset has no fields for promotions, local events, weather, or competitor actions — any of which could explain sudden demand surges. The cause of these spikes remains a hypothesis without external context data.

## Repository Contents

| File | Description |
|---|---|
| `week01_supply_chain_eda.ipynb` | Full EDA notebook — data quality checks, 5 business questions, visualizations |
| `week01_dashboard.png` | 2×3 chart dashboard summarizing all findings |
| `week01_data_quality_report.md` | 1-page data quality report |
| `Wk 01 - Supply Chain Dataset.xlsx` | Raw dataset |

## Tools

Python 3.11 · Pandas · Matplotlib · Seaborn · Jupyter Notebook

## Setup

```bash
pip install -r requirements.txt
jupyter notebook week01_supply_chain_eda.ipynb
```
