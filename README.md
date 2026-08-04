&lt;!-- HEADER SECTION --&gt;
&lt;div align="center"&gt;
  
  # 🏛️ IMF Global Reserves Analytics
  ### Deep-Dive Data Intelligence on International Monetary Fund Reserve Composition, Liquidity Risk & Gold Trends (2019–2026)

  [![SQL](https://img.shields.io/badge/SQL-MySQL%2FPostgreSQL-blue?logo=postgresql)](https://github.com/amriiiita07-ui/IMF-Data-Analysis/blob/main/IMF-Data-Analysis-main/IMF.sql)
  [![PowerBI](https://img.shields.io/badge/PowerBI-Interactive%20Dashboard-yellow?logo=powerbi)](https://github.com/amriiiita07-ui/IMF-Data-Analysis/blob/main/IMF-Data-Analysis-main/IMF_GOLD_RESERVES_REPORT.pbix)
  [![Data](https://img.shields.io/badge/Data-CSV%20%7C%20SQL%20%7C%20PBIX-green?logo=databricks)](https://github.com/amriiiita07-ui/IMF-Data-Analysis/tree/main/IMF-Data-Analysis-main)
  [![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)](LICENSE)

&lt;/div&gt;

---

## 📋 Table of Contents
1. [Project Overview](#-project-overview)
2. [Key Insights at a Glance](#-key-insights-at-a-glance)
3. [Data Architecture](#-data-architecture)
4. [Dataset Dictionary](#-dataset-dictionary)
5. [Analytical Modules](#-analytical-modules)
   - [Module A: Gold Reserves Trend (7 Years)](#module-a--gold-reserves-trend-analysis-20192026)
   - [Module B: Reserve Composition & G20 Benchmarking](#module-b--country-wise-reserve-composition--g20-benchmarking)
   - [Module C: Drain Exposure & Illiquidity Risk](#module-c--drain-exposure--illiquidity-risk-assessment-2026)
   - [Module D: MoM Volatility (Mar–Apr 2026)](#module-d--month-over-month-mom-volatility-march--april-2026)
   - [Module E: SDR Share Evolution](#module-e--sdr-special-drawing-rights-share-evolution-20192026)
   - [Module F: Regional Reserve Distribution](#module-f--regional-share-of-total-reserves-2026)
6. [Power BI Dashboard](#-power-bi-dashboard)
7. [Tech Stack](#-tech-stack)
8. [How to Use](#-how-to-use)
9. [Future Roadmap](#-future-roadmap)
10. [Author](#-author)

---

## 🌐 Project Overview

This project provides a **comprehensive analytical framework** for understanding global foreign reserve dynamics using IMF-standard datasets. It tracks **gold accumulation trends**, **reserve composition shifts**, **liquidity risk exposure**, and **Special Drawing Rights (SDR)** adoption across 150+ economies from **2019 to 2026**.

&gt; **Core Question Answered:** *How liquid, diversified, and stable are the world's central bank reserves?*

---

## 🎯 Key Insights at a Glance

| Metric | Insight | Trend |
|--------|---------|-------|
| **Top Gold Holder** | United States (41.71% of reserves in Gold, 2026) | 📈 +4.7pp since 2019 |
| **Fastest Gold Accumulator** | Bulgaria (33.20% in 2026 vs 2.96% in 2019) | 🚀 +30.24pp |
| **Highest Liquidity Risk** | US, Germany, France (Low Drain Exposure = High Illiquidity) | ⚠️ Illiquid |
| **Biggest MoM Crash** | Italy (-80.05% Mar–Apr 2026) | 🔻 Sharp Decline |
| **SDR Growth Leader** | Croatia (+15.86pp SDR share in 7 years) | 📊 Diversification |
| **Regional Dominance** | "Other" economies hold **82.83%** of global reserves | 🌍 Dispersed |
| **G20 Average** | Gold (13.17%) \| Forex (68.01%) \| SDRs (3.25%) \| IMF (0.57%) | 📋 Benchmark |

---

## 🗂️ Data Architecture

```mermaid
flowchart TD
    A[Raw IMF Data] --&gt;|ETL / SQL| B[(IMF_sql Database)]
    B --&gt; C[GOLD_REPORT.csv]
    B --&gt; D[RESERVES_REPORT_COUNTRYWISE.csv]
    B --&gt; E[DRAIN_EXPOSURE_REPORT_2026.csv]
    B --&gt; F[MOM_CHANGE_2026_MARCH_APRIL.csv]
    B --&gt; G[SDR_SHARE_TREND_7_YEARS.csv]
    B --&gt; H[REGIONAL_SHARE_TOTAL_RESERVES_2026.csv]
    B --&gt; I[G20_AVG_COMPOSITION_2026.csv]
    C --&gt; J[Power BI Dashboard]
    D --&gt; J
    E --&gt; J
    F --&gt; J
    G --&gt; J
    H --&gt; J
    I --&gt; J
