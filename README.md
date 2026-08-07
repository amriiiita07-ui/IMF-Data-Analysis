<div align="center">
  
  # IMF Global Reserves Analytics
  ### Deep-Dive Data Intelligence on IMF Reserve Composition, Liquidity Risk & Gold Trends (2019–2026)

  [![SQL](https://img.shields.io/badge/SQL-MySQL%2FPostgreSQL-blue?logo=postgresql)](https://github.com/amriiiita07-ui/IMF-Data-Analysis/blob/main/IMF-Data-Analysis-main/IMF.sql)
  [![PowerBI](https://img.shields.io/badge/PowerBI-Interactive%20Dashboard-yellow?logo=powerbi)](https://github.com/amriiiita07-ui/IMF-Data-Analysis/blob/main/IMF-Data-Analysis-main/IMF_GOLD_RESERVES_REPORT.pbix)
  [![Data](https://img.shields.io/badge/Data-CSV%20%7C%20SQL%20%7C%20PBIX-green?logo=databricks)](https://github.com/amriiiita07-ui/IMF-Data-Analysis/tree/main/IMF-Data-Analysis-main)

</div>

---

## Table of Contents
1. [Project Overview](https://github.com/amriiiita07-ui/IMF-Data-Analysis/blob/main/#-Project-Overview)
2. [Key Insights at a Glance](#-key-insights-at-a-glance)
3. [Data Architecture](#-data-architecture)
4. [Dataset Dictionary](#-dataset-dictionary)
5. [Analytical Modules](#-analytical-modules)
6. [Power BI Dashboard](#-power-bi-dashboard)
7. [Tech Stack](#-tech-stack)
8. [How to Use](#-how-to-use)
9. [Future Roadmap](#-future-roadmap)
10. [Author](#-author)

---

## Project Overview

This project provides a **comprehensive analytical framework** for understanding global foreign reserve dynamics using IMF-standard datasets. It tracks **gold accumulation trends**, **reserve composition shifts**, **liquidity risk exposure**, and **Special Drawing Rights (SDR)** adoption across 150+ economies from **2019 to 2026**.

&gt; **Core Question Answered:** *How liquid, diversified, and stable are the world's central bank reserves?*

---

## Key Insights at a Glance

| Metric | Insight | Trend |
|--------|---------|-------|
| **Top Gold Holder** | United States (41.71% of reserves in Gold, 2026) | 📈 +4.7pp since 2019 |
| **Fastest Gold Accumulator** | Bulgaria (33.20% in 2026 vs 2.96% in 2019) | 🚀 +30.24pp |
| **Highest Liquidity Risk** | US, Germany, France (Low Drain Exposure = High Illiquidity) | ⚠️ Illiquid |
| **Biggest MoM Crash** | Italy (-80.05% Mar–Apr 2026) | 🔻 Sharp Decline |
| **SDR Growth Leader** | Croatia (+15.86pp SDR share in 7 years) | 📊 Diversification |
| **Regional Dominance** | "Other" economies hold **82.83%** of global reserves | 🌍 Dispersed |
| **G20 Average** | Gold (13.17%) / Forex (68.01%) / SDRs (3.25%) / IMF (0.57%) | 📋 Benchmark |

---

## Data Architecture

```
┌─────────────┐      ETL / SQL      ┌──────────────────┐
│  Raw IMF    │  ----------------&gt;  │   IMF.sql        │
│    Data     │                     │   Database       │
└─────────────┘                     └────────┬─────────┘
                                             │
    ┌────────────────────────────────────────┼────────────────────────┐
    │                                        │                        │
    ▼                                        ▼                        ▼
┌──────────────┐  ┌─────────────────────┐  ┌─────────────────────┐  ┌─────────────────────┐
│ GOLD_REPORT  │  │ RESERVES_REPORT_    │  │ DRAIN_EXPOSURE_     │  │ MOM_CHANGE_2026_    │
│ .csv         │  │ COUNTRYWISE.csv     │  │ REPORT_2026.csv     │  │ MARCH_APRIL.csv     │
└──────────────┘  └─────────────────────┘  └─────────────────────┘  └─────────────────────┘
    │                                        │                        │
    │    ┌─────────────────────┐             │                        │
    │    │ SDR_SHARE_TREND_    │&lt;────────────┘                        │
    │    │ 7_YEARS.csv         │                                      │
    │    └─────────────────────┘                                      │
    │    ┌─────────────────────┐                                      │
    └───&gt;│ REGIONAL_SHARE_     │&lt;─────────────────────────────────────┘
         │ TOTAL_RESERVES_2026 │
         └─────────────────────┘
                          │
                          ▼
              ┌─────────────────────┐
              │  Power BI Dashboard │
              │ IMF_GOLD_RESERVES_  │
              │    REPORT.pbix      │
              └─────────────────────┘
```

---

## Dataset Dictionary

| File Name | Records | Description |
|-----------|---------|-------------|
| `GOLD_REPORT.csv` | 150+ Countries | Gold as % of Total Reserves (2019–2026) |
| `RESERVES_REPORT_COUNTRYWISE.csv` | 150+ Countries | 4-Pillar Composition: Gold, Forex, SDRs, IMF Position |
| `DRAIN_EXPOSURE_REPORT_2026.csv` | 150+ Countries | Liquid Obligations vs Total Reserves & Risk Flags |
| `MOM_CHANGE_2026_MARCH_APRIL.csv` | 100+ Entities | Absolute & Percentage Change in Total Reserves |
| `SDR_SHARE_TREND_7_YEARS.csv` | 97 Countries | SDR Share in 2026 vs 2019 with Percentage-Point Change |
| `REGIONAL_SHARE_TOTAL_RESERVES_2026.csv` | 7 Regions | Regional Aggregation & Global Share % |
| `G20_AVG_COMPOSITION_2026.csv` | 1 Aggregate | G20 Average Benchmark for Composition |
| `IMF.sql` | — | Full relational schema & data insertion scripts |
| `IMF_GOLD_RESERVES_REPORT.pbix` | — | Interactive Power BI visualization |

---

## Analytical Modules

### Module A | Gold Reserves Trend Analysis (2019–2026)

**Objective:** Identify which nations are aggressively "de-dollarizing" or hedging into gold.

**Top 10 Gold-Heavy Economies (2026)**

| Rank | Country | 2026 Gold % | 2019 Gold % | 7-Yr Change |
|:----:|---------|:-----------:|:-----------:|:-----------:|
| 1 | United States | 41.71% | 37.01% | +4.70pp |
| 2 | Germany | 41.56% | 34.79% | +6.77pp |
| 3 | France | 40.50% | 30.11% | +10.39pp |
| 4 | Italy | 40.08% | 32.73% | +7.35pp |
| 5 | Portugal | 39.26% | 28.69% | +10.57pp |
| 6 | Kazakhstan | 38.92% | 27.51% | +11.41pp |
| 7 | Austria | 37.27% | 24.64% | +12.63pp |
| 8 | Netherlands | 36.37% | 32.82% | +3.55pp |
| 9 | Greece | 34.51% | 31.93% | +2.58pp |
| 10 | Türkiye | 33.85% | 10.64% | **+23.21pp** |

&gt; **Insight:** Türkiye and Bulgaria show explosive gold accumulation, suggesting a strategic pivot toward hard assets amid currency volatility.

**Global Gold Trend (World Average)**

| Year | World Avg Gold % | Visual |
|:----:|:----------------:|:------:|
| 2019 | 5.31% | ███░░░░░░░░░░░░░░░░░ |
| 2020 | 6.55% | ████░░░░░░░░░░░░░░░░ |
| 2021 | 6.38% | ████░░░░░░░░░░░░░░░░ |
| 2022 | 7.03% | ████░░░░░░░░░░░░░░░░ |
| 2023 | 7.52% | █████░░░░░░░░░░░░░░░ |
| 2024 | 8.22% | █████░░░░░░░░░░░░░░░ |
| 2025 | 10.81% | ███████░░░░░░░░░░░░░ |
| 2026 | **14.01%** | █████████░░░░░░░░░░░ |

---

### Module B | Country-Wise Reserve Composition & G20 Benchmarking

**Objective:** Compare any country's reserve "mix" against the G20 average.

**G20 Average Benchmark (2026)**

| Component | Percentage | Visual Bar |
|-----------|:----------:|:----------:|
| Gold | 13.17% | ████████████░░░░░░░░ |
| Forex | 68.01% | ████████████████████████████████████████████████████████ |
| SDRs | 3.25% | ███░░░░░░░░░░░░░░░░░ |
| IMF | 0.57% | █░░░░░░░░░░░░░░░░░░░ |

**Composition Extremes**

| Country | Gold % | Forex % | SDRs % | IMF % | Profile |
|---------|:------:|:-------:|:------:|:-----:|---------|
| United States | 41.71 | 51.27 | 5.93 | 1.08 | Gold-Heavy |
| Germany | 41.56 | 53.15 | 4.51 | 0.78 | Gold-Heavy |
| China | 4.57 | 94.54 | 0.74 | 0.15 | Forex-Dominant |
| Japan | 4.56 | 92.84 | 2.20 | 0.40 | Forex-Dominant |
| Luxembourg | 5.45 | 53.07 | **33.86** | 7.62 | SDR-Heavy |
| Maldives | 0.35 | **99.40** | 0.01 | 0.24 | Ultra-Liquid |

---

### Module C | Drain Exposure & Illiquidity Risk Assessment (2026)

**Objective:** Measure what portion of reserves is tied to liquid obligations vs truly available assets.

&gt; **Formula:** `DRAIN_EXPOSURE_PCT = (LIQUID_OBLIGATIONS / TOTAL_RESERVES) * 100`
&gt; 
&gt; **Interpretation:** A *low* drain exposure implies the country holds illiquid assets (e.g., physical gold) — flagged as **HIGH ILLIQUIDITY RISK**. A *high* drain exposure implies reserves are liquid/accessible.

| Risk Category | Drain Exposure | Count | Examples |
|:-------------:|:--------------:|:-----:|----------|
| **HIGH ILLIQUIDITY RISK** | &lt; 30% | 15 | USA (9.65%), Germany (11.69%), France (12.44%) |
| **OK (Liquid)** | &gt; 30% | 80+ | Switzerland (84.90%), Japan (88.28%), China (89.98%) |

**Illiquidity Risk Spectrum (Selected Nations)**

| Country | Drain Exposure % | Risk Level | Visual |
|---------|:----------------:|:----------:|:------:|
| United States | 9.65% | High Illiquidity | ██░░░░░░░░░░░░░░░░░░ |
| Germany | 11.69% | High Illiquidity | ██░░░░░░░░░░░░░░░░░░ |
| France | 12.44% | High Illiquidity | ██░░░░░░░░░░░░░░░░░░ |
| Italy | 15.65% | High Illiquidity | ███░░░░░░░░░░░░░░░░░ |
| Türkiye | 29.87% | High Illiquidity | █████░░░░░░░░░░░░░░░ |
| Belarus | 43.03% | OK | ████░░░░░░░░░░░░░░░░ |
| India | 79.87% | OK | ███████████████░░░░░ |
| China | 89.98% | OK | █████████████████░░░ |
| Japan | 88.28% | OK | █████████████████░░░ |
| Korea | 94.26% | OK | ███████████████████░ |

&gt; **Insight:** Advanced economies (US, EU) hold massive gold stockpiles, making them "illiquid" on paper but strategically secure. Emerging markets maintain higher forex liquidity for trade stability.

---

### Module D | Month-over-Month (MoM) Volatility: March to April 2026

**Objective:** Detect acute reserve shocks, interventions, or data anomalies.

**Top Gainers (Mar–Apr 2026)**

| Rank | Country | Apr 2026 | Mar 2026 | Change | % Change |
|:----:|---------|----------|----------|--------|----------|
| 1 | Panama | $11.76B | $9.25B | +$2.51B | **+27.11%** |
| 2 | Angola | $28.36B | $25.57B | +$2.79B | **+10.92%** |
| 3 | Costa Rica | $41.77B | $38.52B | +$3.25B | **+8.43%** |
| 4 | El Salvador | $10.39B | $9.98B | +$0.41B | +4.10% |
| 5 | Armenia | $11.40B | $11.10B | +$0.30B | +2.68% |

**Top Losers (Mar–Apr 2026)**

| Rank | Country | Apr 2026 | Mar 2026 | Change | % Change |
|:----:|---------|----------|----------|--------|----------|
| 1 | Italy | $181.3B | $908.7B | **-$727.4B** | **-80.05%** |
| 2 | Kazakhstan | $30.1B | $135.0B | -$104.9B | -77.74% |
| 3 | Türkiye | $112.7B | $304.3B | -$191.6B | -62.96% |
| 4 | Maldives | $1.41B | $2.67B | -$1.26B | -47.10% |
| 5 | Poland | $416.6B | $583.7B | -$167.1B | -28.62% |

&gt; **Insight:** Several major economies (Italy, Turkey, Kazakhstan) show extreme drawdowns. This may indicate central bank intervention to defend currency, debt servicing, or gold revaluation adjustments.

---

### Module E | SDR (Special Drawing Rights) Share Evolution (2019 to 2026)

**Objective:** Track IMF SDR allocation adoption as a diversification tool.

**Biggest SDR Adopters (Percentage-Point Gain)**

| Rank | Country | 2026 SDR % | 2019 SDR % | pp Change |
|:----:|---------|:----------:|:----------:|:---------:|
| 1 | Croatia | 16.90% | 1.04% | **+15.86** |
| 2 | Luxembourg | 33.86% | 18.57% | **+15.29** |
| 3 | Ireland | 21.39% | 8.87% | **+12.51** |
| 4 | Bulgaria | 11.00% | 1.53% | **+9.47** |
| 5 | Estonia | 8.88% | 1.83% | **+7.05** |

**SDR Decliners (Strategic Shift Away)**

| Rank | Country | 2026 SDR % | 2019 SDR % | pp Change |
|:----:|---------|:----------:|:----------:|:---------:|
| 1 | Zimbabwe | 0.24% | 7.89% | **-7.65** |
| 2 | Argentina | 0.05% | 2.54% | **-2.49** |
| 3 | Netherlands | 7.43% | 8.69% | -1.26 |
| 4 | Pakistan | 0.22% | 1.25% | -1.04 |
| 5 | El Salvador | 2.12% | 3.00% | -0.88 |

---

### Module F | Regional Share of Total Reserves (2026)

**Objective:** Understand geopolitical concentration of global wealth.

| Rank | Region | Countries | Total Reserves (USD) | Global Share % | Visual |
|:----:|--------|:---------:|:--------------------:|:--------------:|:------:|
| 1 | Other / Unclassified | 156 | $1,372,017,177,700 | **82.83%** | ████████████████████ |
| 2 | Asia-Pacific | 9 | $147,589,048,500 | 8.91% | ██░░░░░░░░░░░░░░░░░░ |
| 3 | Europe | 9 | $63,472,147,000 | 3.83% | █░░░░░░░░░░░░░░░░░░░ |
| 4 | Americas | 8 | $44,928,229,000 | 2.71% | █░░░░░░░░░░░░░░░░░░░ |
| 5 | Middle East | 5 | $18,596,995,100 | 1.12% | ░░░░░░░░░░░░░░░░░░░░ |
| 6 | Africa | 6 | $5,651,383,400 | 0.34% | ░░░░░░░░░░░░░░░░░░░░ |
| 7 | Eastern Europe & CIS | 3 | $4,085,643,400 | 0.25% | ░░░░░░░░░░░░░░░░░░░░ |

&gt; **Insight:** The "Other" category's dominance (82.83%) reflects the long-tail distribution where 156 smaller/individual economies collectively outweigh regional blocs.

---

## Power BI Dashboard

The `IMF_GOLD_RESERVES_REPORT.pbix` file contains an interactive dashboard with:

- **KPI Cards:** Total Global Reserves, Average Gold %, SDR Allocation
- **Country Slicer:** Drill-down by individual nation
- **Time Series:** 7-year gold trend lines
- **Risk Matrix:** Drain Exposure vs Total Reserves scatter plot
- **Regional Treemap:** Visual share of reserves by geography
- **MoM Waterfall:** March to April 2026 change visualization

&gt; **Tip:** Open with **Power BI Desktop** to refresh data or publish to Power BI Service for sharing.

---

## Tech Stack

| Layer | Technology | Purpose |
|-------|------------|---------|
| **Database** | SQL (MySQL/PostgreSQL compatible) | Schema design, relational integrity, complex joins |
| **Data Processing** | Python / Pandas (implied) | CSV generation, cleaning, transformation |
| **Visualization** | Power BI | Interactive dashboards & executive reporting |
| **Version Control** | Git + GitHub | Collaboration & data lineage |

---

## How to Use

**Step 1 — Clone the Repository**

```
git clone https://github.com/amriiiita07-ui/IMF-Data-Analysis.git
cd IMF-Data-Analysis/IMF-Data-Analysis-main
```

**Step 2 — Setup the Database**

```
# For MySQL
mysql -u root -p &lt; IMF.sql

# For PostgreSQL
psql -U postgres -f IMF.sql
```

**Step 3 — Explore CSVs in Python**

```python
import pandas as pd

# Load Gold Report
df_gold = pd.read_csv("GOLD_REPORT.csv")

# Quick insight: Top 5 gold accumulators since 2019
df_gold['CHANGE'] = df_gold['GOLD_PERCENTAGE_2026'] - df_gold['GOLD_PERCENTAGE_2019']
top5 = df_gold.nlargest(5, 'CHANGE')[['COUNTRY', 'CHANGE']]
print(top5)
```

**Step 4 — Open Power BI Report**

- Launch `IMF_GOLD_RESERVES_REPORT.pbix` in **Power BI Desktop**
- Click **Refresh** to sync with your local SQL instance (if connected)

---

## Future Roadmap

- [ ] **Automated ETL Pipeline:** Python script to pull live IMF COFER data via API
- [ ] **Currency Risk Model:** Correlation matrix between USD strength and Forex reserve ratios
- [ ] **Predictive Forecasting:** ARIMA/Prophet models for 2027 gold share projections
- [ ] **Web Dashboard:** Streamlit or React frontend for browser-based exploration
- [ ] **PDF Report Generator:** Automated executive summary export

---

## Author

**Amrita Singh** ([@amriiiita07-ui](https://github.com/amriiiita07-ui))

&gt; *"Data is the new gold, but only if you know how to refine it."*

---

<div align="center">
  
  **Star this repo if you found it insightful!**
  
  *Built with curiosity, SQL, and a lot of coffee.*

</div>
