# Bank Financial Performance & Risk Analytics

End-to-end financial risk analytics project analysing 2,512 bank transactions using Python, MySQL, and Power BI — featuring anomaly 
detection, MoM growth analysis, and an interactive executive dashboard.

Aligned to financial risk oversight and analytics frameworks used at firms like American Express, ZS Associates, and BFSI consulting teams.


---

## Project Objective

Financial institutions generate thousands of transactions daily — 
but which ones carry risk? This project builds an end-to-end 
analytics pipeline to answer:

- Which transactions are statistically anomalous and why?
- How do monthly transaction volumes trend and grow over time?
- Which customer segments hold the highest balances and risk exposure?
- Where does geographic and channel-level performance concentrate?

---

## Dataset Overview

| Column | Description |
|---|---|
| TransactionID | Unique transaction identifier |
| AccountID | Customer account reference |
| TransactionAmount | Amount in USD |
| TransactionDate | Date and time of transaction |
| TransactionType | Debit or Credit |
| Location | US city of transaction |
| Channel | ATM, Online, or Branch |
| CustomerAge | Age of account holder |
| CustomerOccupation | Doctor, Engineer, Retired, Student |
| AccountBalance | Current account balance in USD |
| LoginAttempts | Number of login attempts before transaction |

Total records: 2,512 transactions · 495 accounts · 43 locations

---

## Phase 1 — Python: Data Cleaning & Feature Engineering

Libraries: Pandas, NumPy

5 features engineered:

| Feature | Description | Result |
|---|---|---|
| DaysSinceLastTxn | Gap between transactions | Avg 488 days |
| BalanceUtilisationPct | Transaction as % of balance | Avg 20% |
| AmountPerMinute | Transaction speed | Velocity indicator |
| IsAnomaly | 2 standard deviation flag | 121 flagged (4.8%) |
| IsHighRisk | Anomaly + login attempts > 2 | 3 flagged |

Output: Clean 22-column dataset exported as bank_clean.csv

---

## Phase 2 — SQL: 5 Advanced Queries

| # | Query | Techniques Used |
|---|---|---|
| 1 | Monthly Transaction Volume Trend | GROUP BY, Window Function |
| 2 | Top 10 High-Value Customers | RANK() OVER |
| 3 | Transaction Breakdown by Location | PARTITION BY |
| 4 | Anomalous Accounts by Risk Level | HAVING, aggregations |
| 5 | Month-over-Month Growth Rate | CTE + LAG() Window Function |

---

## Phase 3 — Power BI: Executive Dashboard

6 KPI Cards: Total Transactions · Total Volume · Avg Account Balance · 
Anomalous Transactions · High Risk Accounts · Anomaly Rate %

Visuals:
- Monthly transaction volume trend (line chart)
- Transaction type breakdown (donut)
- Avg balance by occupation (bar)
- Top 10 locations by volume (bar)
- High risk account monitor (table with filters)
- Customer occupation slicer / Transaction type slicer

---

## Key Findings

**Finding 1 — May was the highest-risk growth month**
- May recorded +53.3% MoM growth — the steepest spike in the dataset.
- CTE and LAG() analysis across 12 months showed May as a 2x outlier vs the annual average monthly growth rate.
- Sudden volume spikes without a corresponding rise in anomaly rate suggest potential reporting lag or delayed fraud detection.
- Overlay anomaly flags with MoM growth to identify disguised fraud surges.

**Finding 2 — Doctors dominate high-balance accounts**
- All top 10 high-balance accounts belong to Doctors, averaging ~$14,700.
- This is nearly 3x the overall portfolio average of $5,114, yet their balance utilisation per transaction is only 10–13%.
- High balance + low utilisation = high-value, low-risk segment — ideal for premium product targeting.
- Segment Doctor accounts separately for retention and cross-sell strategy.

**Finding 3 — Three accounts show 100% anomaly rate**
- AC00083 (Student, San Diego) averages $1,531 per transaction — the strongest single-account fraud signal in the dataset.
- All 3 flagged accounts have login attempts > 2 combined with transaction amounts > 2 standard deviations from the mean.
- Student occupation + high transaction amount + elevated login attempts is a compound risk pattern not visible from any single metric.
- Implement compound risk scoring combining anomaly flag, login attempts, and occupation baseline for account-level monitoring.

**Finding 4 — ATM dominates all top 10 locations**
- ATM is the primary channel across all top 10 cities by transaction volume.
- Oklahoma City Online users average $432 per transaction, the highest of any channel-location combination in the dataset.
- Online channel in mid-size cities shows disproportionate transaction value, warrants targeted fraud monitoring beyond volume-based alerts.
- Build channel × location risk matrix; apply higher scrutiny to online transactions in cities with elevated per-transaction averages.

---

## Tools & Techniques

| Tool | Usage |
|---|---|
| Python (Pandas, NumPy) | Data cleaning, feature engineering, anomaly detection |
| MySQL Workbench | Database setup, SQL querying |
| Power BI Desktop | Dashboard development, DAX measures |

---
