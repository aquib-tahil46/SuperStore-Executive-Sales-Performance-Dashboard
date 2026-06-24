# 📊 SuperStore Executive Sales Performance Dashboard

An end-to-end **Power BI** project that transforms raw SuperStore transactional data into an executive-level sales performance dashboard with a **15-day sales forecast**.

![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Calculated%20Columns-blue)
![Power Query](https://img.shields.io/badge/Power%20Query-Data%20Prep-orange)

---

## 🎯 Project Objective

Retail leadership needs a single, reliable view of sales, profit, and operational performance — without digging through raw transaction logs. This dashboard answers:

- Which regions, segments, and categories drive the most revenue?
- Where is profit concentrated or leaking by month?
- How efficient are delivery and fulfillment channels?
- What does demand look like over the next 15 days?
---

## 📊 Dashboard Preview

![Executive Sales Performance Dashboard](https://github.com/user-attachments/assets/5cc75467-dbb8-4fbc-9b32-9782ed84d002)
*Executive Sales Performance Dashboard*

![SuperStore Sales Forecast](https://github.com/user-attachments/assets/10cd1df3-c4d4-40fd-b6d1-4eccadbda39f)
*SuperStore Sales Forecast — 15 Days*

---

## 🗂️ Dataset

- **Source:** SuperStore Sales Dataset (retail transactions)
- **Scale:** ~3,000 orders
- **Grain:** One row per order line item
- **Key fields:** Order ID, Order Date, Ship Date, Ship Mode, Customer, Segment, Region, State, City, Category, Sub-Category, Sales, Quantity, Profit, Returns, Payment Mode

---

## 🏗️ Data Model

The model is built around a single transactional fact table (`SuperStore_Sales_Dataset`) connected to dedicated **date tables** for both Order Date and Ship Date, plus a separate `Forecast` table feeding the forecast visual.

```
SuperStore_Sales_Dataset
 ├── Order Date  → Date Table (Order)
 └── Ship Date   → Date Table (Ship)

Forecast
 └── Order Date  → Date Table (Forecast)
```

**Calculated columns (DAX):**
```DAX
Avg Delivery = DATEDIFF(SuperStore_Sales_Dataset[Order Date], SuperStore_Sales_Dataset[Ship Date], DAY)
Total Sales  = SUM(SuperStore_Sales_Dataset[Sales])
```

Date table fields (Year, MonthNo, Month, QuarterNo, Quarter, Day) support all time-intelligence visuals (Sales by Month, Profit by Month).

---

## 📈 Dashboard Pages

### Page 1 — Executive Sales Performance Dashboard
| KPI | Value |
|---|---|
| Orders | 3K |
| Sales | $2M |
| Profit | $175K |
| Quantity | 22K |
| Avg. Delivery | 4 days |

**Visuals:**
- Sales & Profit by Month (2019 vs 2020 trend comparison)
- Sales by Category & Sub-Category (bar + treemap)
- Sales by Region (Central / East / South / West) with slicer
- Sales by Segment (Consumer / Corporate / Home Office) — donut
- Sales & Profit by State — map visual
- Sales by Ship Mode — donut (Standard Class leads at 58.3%)
- Sales by Payment Mode — COD vs Cards/Online

### Page 2 — SuperStore Sales Forecast (15 Days)
- Power BI native forecasting applied to the daily sales time series
- Confidence interval band around the 15-day projection
- Zoomable trend line (Nov 2020 – Jan 2021 focus window)
- Top 10 states by sales, ranked

---

## 💡 Key Insights

- **West region** leads sales (~$0.52M), followed by East (~$0.45M)
- **Consumer segment** contributes the largest share of sales (~48%)
- **Standard Class** shipping accounts for the majority of order volume (58.3%)
- **Phones** and **Chairs** are the top revenue-generating sub-categories
- **California, New York, Texas** are the top 3 states by sales
- **COD** is the dominant payment mode at 51.6% of transactions

---

## 🛠️ Tools & Techniques Used

- **Power Query (M):** Data cleaning, type transformations, shaping the source dataset
- **Data Modeling:** Single fact table with role-playing date dimensions (Order Date / Ship Date)
- **DAX:** Calculated columns for delivery time and sales aggregation
- **Power BI Forecasting:** Built-in exponential smoothing forecast on the sales time series
- **Visuals:** Map, TreeMap, Donut, Combo (line + clustered column), Card KPIs, Slicers

---

## 📁 Repository Contents

| File | Description |
|---|---|
| `SuperStore_Sales_Dashboard.pbit` | Power BI template file (open in Power BI Desktop) |
| `SuperStore_Sales_Dashboard.pdf` | Static export of both dashboard pages |
| `screenshots/` | Dashboard preview images |

---

## 🚀 How to Use

1. Download `SuperStore_Sales_Dashboard.pbit`
2. Open in **Power BI Desktop**
3. Load/connect the SuperStore dataset when prompted
4. Explore — use the Region slicer and date filters to drill into specific segments

---

## 👤 Author

**Aquib Tahil**
BI & Data Analyst | Tableau · Power BI · SQL
[Tableau Public](https://public.tableau.com/app/profile/aquib.tahil8642) · [GitHub](https://github.com/aquib-tahil46)

---

*Built as part of an ongoing portfolio of BFSI and retail analytics projects.*
