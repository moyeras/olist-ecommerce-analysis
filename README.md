# 🛒 Olist E-Commerce Sales Analysis

> End-to-end data analytics project built on real Brazilian e-commerce data from [Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — covering data exploration, cleaning, SQL analysis, and an interactive Power BI dashboard.

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| Data Exploration & Cleaning | Python (pandas, numpy, matplotlib, seaborn) |
| Database | PostgreSQL |
| SQL Analysis | Window Functions, CTEs, RFM Segmentation |
| Dashboard | Power BI Desktop |
| Version Control | Git & GitHub |

---

## 📁 Project Structure

```
olist-ecommerce-analysis/
│
├── notebooks/
│   ├── 01_exploration.ipynb       # Data loading, null analysis, type inspection
│   ├── 02_cleaning.ipynb          # Date parsing, null handling, feature engineering
│   └── 03_sql_analysis.ipynb      # PostgreSQL connection, query execution
│
├── powerbi/
│   ├── olist_dashboard.pbix       # Power BI dashboard file
│   ├── monthly_revenue.png        # Chart export
│   ├── category_performance.png   # Chart export
│   ├── delivery_performance.png   # Chart export
│   └── rfm_segments.png           # Chart export
│
├── .gitignore
└── README.md
```

---

## 📊 Analysis Overview

### 1. 📈 Monthly Revenue & Order Trends
- Tracked revenue and order volume across 2016–2018
- Identified **November 2017 Black Friday spike** — highest single month at **1.15M BRL** and **7,289 orders**
- Clear growth trend from Q4 2016 through mid 2017

### 2. 🏷️ Category Performance
- Analyzed top 15 product categories by revenue, avg item price and review score
- **beleza_saude** (beauty & health) leads at **1.2M BRL** with a strong **4.19** avg review score
- **moveis_escritorio** (office furniture) flagged — high revenue but lowest review score at **3.52**

### 3. 🚚 Delivery Performance by State
- Calculated late delivery rate and avg delivery days per Brazilian state
- **AL, MA, SE** worst performers — all above **20% late delivery rate**
- **SP** (São Paulo) most efficient — **8.3 avg days**, **5.77% late rate**
- Remote Amazon states **(RR, AP)** average **27+ days** delivery

### 4. 👥 RFM Customer Segmentation
Customers scored on **Recency, Frequency, Monetary** value and grouped into 8 segments:

| Segment | Customers | Avg Spend |
|---|---|---|
| Lost | 22,538 | 62 BRL |
| Loyal | 17,266 | 258 BRL |
| Recent Customer | 12,042 | 64 BRL |
| Potential Loyalist | 11,785 | 64 BRL |
| At Risk | 11,838 | 260 BRL |
| Cannot Lose Them | 1,198 | 270 BRL |
| Champion | 5,585 | 294 BRL |
| Hibernating | 314 | 138 BRL |

---

## 🗄️ Key SQL Concepts Used

- `DATE_TRUNC` for monthly time series grouping
- `NTILE(4)` window function for RFM scoring
- `CASE WHEN` for conditional segmentation logic
- Multi-table JOINs across 7 related tables
- CTEs (`WITH`) for readable multi-step queries
- `OVER()` window functions for ranking without collapsing rows

---

## 🐍 Python Feature Engineering

New columns created during cleaning:

| Column | Logic |
|---|---|
| `delivery_days` | `order_delivered_customer_date` - `order_purchase_timestamp` |
| `is_late` | `1` if delivered after estimated date, else `0` |
| `order_month` | Extracted from `order_purchase_timestamp` |

---

## 📦 Dataset

- **Source:** [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Size:** ~100K orders, 7 related tables
- **Period:** 2016 – 2018

> ⚠️ Raw data files are not included in this repo. Download from Kaggle and place CSVs in a `files/` folder.

---

## 🚀 How to Run

1. Clone the repo
```bash
git clone https://github.com/moyeras/olist-ecommerce-analysis.git
```

2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn sqlalchemy psycopg2-binary
```

3. Download dataset from Kaggle and place CSVs in `files/`

4. Create a PostgreSQL database named `olist`

5. Run notebooks in order:
   - `01_exploration.ipynb`
   - `02_cleaning.ipynb`
   - `03_sql_analysis.ipynb`

6. Open `powerbi/olist_dashboard.pbix` in Power BI Desktop

---

## 👤 Author

**Yusuf** — CS Graduate | Data & Analytics  
[GitHub](https://github.com/moyeras)
