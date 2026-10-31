# olist-ecommerce-powerbi-analytics
An end-to-end Power BI dashboard analyzing 100k+ Olist e-commerce orders in Brazil. Highlights payment types, temporal trends, delivery freight, and product category sales performance using custom DAX modeling and Power Query ETL.  Markdown
# 📊 Olist E-Commerce Analytics Dashboard | Power BI

An interactive Business Intelligence solution built in **Power BI** to analyze over 100,000 order records from **Olist**, the largest department store marketplace in Brazil. 

This multi-page dashboard delivers deep visual insights into **Payments Overview**, **Time Overview**, and **Sales Performance**, tracking key metrics like Total Sales, Total Orders, Average Items Per Order, and Average Review Scores[cite: 1, 2, 3].

---

## 📌 Executive Summary & Key Dashboard Metrics

* **Macro KPIs:** Tracks 13.59M+ Total Sales, 99K Total Orders, 1.13 Average Items Per Order, and a 4.09 Average Review Score[cite: 1].
* **Payments Overview:** Analyzes transaction breakdown across payment types (credit card dominating at ~78%, followed by boleto, voucher, and debit card) and payment installments[cite: 1, 3].
* **Time Overview:** Breaks down revenue trends by Day, Month, Quarter, and Year to uncover seasonal peaks and temporal sales behavior[cite: 2, 3].
* **Sales & Freight Performance:** Evaluates top-performing product categories (`health_beauty`, `watches_gifts`, `bed_bath_table`) and freight distribution across Brazilian states[cite: 1, 3].

---

## 🗂️ Dashboard Navigation & Pages

1. **Payments Overview:** Features a payment type distribution donut chart, review score distribution histograms, revenue by product category, and a state-level geographic map[cite: 1].
2. **Time Overview:** Highlights granular temporal trends including Total Sales by Day, Month, Quarter, and Year with interactive date and customer state filters[cite: 2].
3. **Sales Performance:** Focuses on monthly payment behavior, total sales by payment installments, and freight cost distribution across customer states and product categories[cite: 3].

---

## 📐 Key DAX Measures & Calculations

```dax
// 1. Total Sales Revenue
Total Sales = 
SUMX(
    FactOrderItems, 
    FactOrderItems[price] + FactOrderItems[freight_value]
)

// 2. Total Delivered Orders
Total Orders = 
CALCULATE(
    COUNTROWS(FactOrders)
)
├── data/
│   └── olist_public_dataset_schema.md  # Schema definitions and data sources
├── reports/
│   └── Olist_Ecommerce_Analytics.pbix  # Power BI Desktop report file
├── screenshots/
│   ├── payments_overview.png           # Payments overview page preview
│   ├── time_overview.png               # Time overview page preview
│   └── sales_performance.png           # Sales performance page preview
└── README.md                           # Project documentation

// 3. Average Review Score
Average Review Score = -
AVERAGE(FactReviews[review_score])
