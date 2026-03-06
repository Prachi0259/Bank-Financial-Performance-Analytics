# 🏦 Bank Financial Performance & Risk Analytics

> End-to-end financial risk analytics project analysing 2,512 bank transactions using Python, MySQL, and Power BI — featuring anomaly detection, MoM growth analysis, and an interactive executive dashboard.

---

## 🔗 Links

[![Portfolio](https://img.shields.io/badge/Portfolio-Live%20Site-orange?style=flat)](https://prachi0259.github.io/Bank-Financial-Performance-Analytics/bank_analytics_portfolio.html)
[![Power BI](https://img.shields.io/badge/Power%20BI-Live%20Dashboard-yellow?style=flat&logo=powerbi)](https://app.powerbi.com/groups/me/reports/bfbdf373-48f2-4169-ad20-b23e1e9dc0a9/69aeffc2546ac0945430?experience=power-bi)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Prachi-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/prachi252/)
[![GitHub](https://img.shields.io/badge/GitHub-Prachi0259-black?style=flat&logo=github)](https://github.com/Prachi0259)

---

## 📸 Dashboard Preview

![Power BI Dashboard](screenshots/dashboard.png)

---

## 🎯 Project Objective

Financial institutions generate thousands of transactions daily — but which ones carry risk? This project builds an end-to-end analytics pipeline to answer:

- Which transactions are statistically anomalous and why
- How monthly transaction volumes trend and grow over time
- Which customer segments hold the highest balances and risk exposure
- Where geographic and channel-level performance concentrates

---

## 🗂️ Project Structure

```
Bank-Financial-Performance-Analytics/
│
├── bank_analytics_portfolio.html    # Interactive portfolio site
├── notebooks/
│   └── bank_cleaning.ipynb          # Python data cleaning & feature engineering
├── sql/
│   └── bank_queries.sql             # All 5 SQL queries
├── data/
│   └── bank_clean.csv               # Cleaned dataset (exported from Python)
├── screenshots/
│   └── dashboard.png                # Power BI dashboard screenshot
└── README.md
```

---

## 📂 Dataset Overview

| Column | Description |
|--------|-------------|
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

**Total Records:** 2,512 transactions · 495 accounts · 43 locations

---

## ⚙️ Phase 1 — Python: Data Cleaning & Feature Engineering

**Libraries used:** Pandas, NumPy, Matplotlib

**5 new features engineered:**

| Feature | Description | Result |
|---------|-------------|--------|
| DaysSinceLastTxn | Gap between transactions | Avg 488 days |
| BalanceUtilisationPct | Transaction as % of balance | Avg 20% |
| AmountPerMinute | Transaction speed | Velocity indicator |
| IsAnomaly | 2 std deviation flag | 121 flagged (4.8%) |
| IsHighRisk | Anomaly + login attempts > 2 | 3 flagged |

**Key output:** Clean 22-column dataset exported as `bank_clean.csv` for SQL import.

---

## 🗄️ Phase 2 — SQL: 5 Advanced Queries

| # | Query | Techniques Used |
|---|-------|----------------|
| 1 | Monthly Transaction Volume Trend | GROUP BY, Window Function |
| 2 | Top 10 High-Value Customers | RANK() OVER |
| 3 | Transaction Breakdown by Location | PARTITION BY |
| 4 | Anomalous Accounts by Risk Level | HAVING, aggregations |
| 5 | Month-over-Month Growth Rate | CTE + LAG() Window Function |

---

## 📊 Phase 3 — Power BI: Executive Dashboard

**6 KPI Cards:** Total Transactions · Total Volume · Avg Account Balance · Anomalous Transactions · High Risk Accounts · Anomaly Rate %

**Visuals:**
- Monthly transaction volume trend (line chart)
- Transaction type breakdown (donut)
- Avg balance by occupation (bar)
- Top 10 locations by volume (bar)
- High risk account monitor (table with filters)
- Customer occupation slicer
- Transaction type slicer

---

## 💡 Key Findings

**May recorded the sharpest MoM growth at +53.3%** — identified through CTE and LAG() Window Function analysis on monthly transaction data across the full year.

**All top 10 high-balance accounts belong to Doctors**, averaging ~$14,700 — nearly 3x the overall average of $5,114, yet with only 10–13% balance utilisation per transaction.

**Top 3 anomalous accounts show 100% anomaly rate** — AC00083 (Student, San Diego) averages $1,531 per transaction, the strongest fraud signal in the dataset.

**ATM dominates as the primary channel** across all top 10 locations, whilst Oklahoma City Online users average $432 per transaction — the highest of any channel-location combination.

**August and September are peak months** at $71K and $72K total volume respectively, with back-to-back +21% MoM growth — the strongest consecutive run of the year.

---

## 🛠️ Tools & Techniques

| Tool | Usage |
|------|-------|
| Python (Pandas, NumPy) | Data cleaning, feature engineering, anomaly detection |
| MySQL Workbench | Database setup, SQL querying |
| Power BI Desktop | Dashboard development, DAX measures |
| Google Colab | Python notebook environment |
| GitHub Pages | Portfolio hosting |

---

## 🚀 How to Run

**Python (Google Colab):**
1. Open `notebooks/bank_cleaning.ipynb` in Google Colab
2. Upload the raw dataset when prompted
3. Run all cells to generate `bank_clean.csv`

**SQL (MySQL Workbench):**
1. Create database: `CREATE DATABASE bank_analysis;`
2. Import `bank_clean.csv` via Table Data Import Wizard
3. Run queries from `sql/bank_queries.sql`

**Power BI:**
1. Open Power BI Desktop
2. Get Data → Text/CSV → select `bank_clean.csv`
3. Load and explore the dashboard

---

## 👩‍💻 Author

**Prachi**
📧 prachi7.work@gmail.com

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/prachi252/)
[![GitHub](https://img.shields.io/badge/GitHub-black?style=flat&logo=github)](https://github.com/Prachi0259)
