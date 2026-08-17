# Week 01 Data Quality Report
Ubuntu AnalytiQ – Nairobi Supply Chain Dataset

## Data Quality Score: 100.0%

The dataset (4,500 rows × 12 columns, covering Jan 2023 – Dec 2024) passed all three checks cleanly:

 Check : Result 
 Missing values: 0 across all 12 columns 
 Units_Received > Units_Ordered (logical anomaly): 0 rows 
 Duplicate TransactionIDs: 0 

## Top 3 Data Issues Found

1. No missing data anywhere. Every column — including Date, Supplier, and Lead_Time_Days — is fully populated, so no imputation or row-dropping was needed.
2. No fulfillment anomalies. Not a single transaction shows more units received than ordered, meaning the supplier fulfillment figures can be trusted at face value without a cleanup step.
3. No duplicate transactions. Each of the 4,500 rows has a unique TransactionID, so aggregate counts (e.g. stockout events per region) are not being inflated by repeated records.

In short: this is an unusually clean dataset, which is good news, but it's also worth flagging as a caveat — real-world Nairobi distributor data would typically have some missingness or logging errors, so this may be a simulated/curated dataset rather than raw operational data.

## Top 3 Business Insights

1. Dairy is the highest stockout-risk category. Dairy has the highest stockout rate (~6.7%) of all 14 categories, nearly double the rate of Baby products (~4.9%) and well above Grain and Flour (~2.0–2.4%). Given dairy's short shelf life, this is the category most worth prioritizing for automated stockout prevention.
2. Westlands is the worst-performing region. Westlands recorded the most stockout events (28) over the two-year period, followed by Thika Road (26) and Mombasa Road (25). Eastleigh had the fewest (20). This points to a regional distribution or demand-forecasting gap rather than a single supplier issue, since lead times and fulfillment rates are fairly consistent across suppliers.
3. Supplier performance is fairly even — no single "bad" supplier. Average lead times cluster tightly between 11.2 and 11.8 days, and fulfillment rates all sit around 92–93%. This suggests stockouts are driven more by demand spikes and regional stocking gaps than by one underperforming supplier.

## One Question the Data Cannot Answer

Why did stockouts spike sharply in certain months (e.g. the peak of 13 events around mid-2023)? The dataset records *that* a stockout happened and *where*, but it has no fields for promotional activity, local events, weather disruptions, or competitor actions — any of which could explain sudden demand surges. Without external context data, the cause of these spikes remains a hypothesis, not a confirmed finding.
