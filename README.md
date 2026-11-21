# Mobile-Sales-Dashboard-Power-BI
Interactive Power BI dashboard analyzing mobile phone sales by brand, model, city &amp; payment method, with MTD and Same-Period-Last-Year time-intelligence reports using DAX.

---
## 📌 Project Overview

This project turns raw mobile sales transactions into an easy-to-explore, three-page report. It helps answer questions like:

- How much revenue and quantity are we selling, and at what average price?
- Which **brands** and **mobile models** perform best?
- Which **cities** generate the most sales?
- How do customers prefer to **pay**?
- How satisfied are customers (ratings breakdown)?
- How are sales trending **month-to-date**, and how do they compare with the **same period last year**?

---

## 📊 Dashboard Pages

### 1. Dashboard (Main Overview)
- **KPI cards:** Total Sales, Total Quantity, Total Transactions, Average Price
- **Map:** Sales by City
- **Funnel chart:** Customer ratings by rating status
- **Line chart:** Quantity sold by month
- **Pie chart:** Transactions by payment method
- **Bar chart:** Total Sales by mobile model
- **Area chart:** Sales by day of the week
- **Table:** Brand-wise sales and transactions
- **Slicers:** Month, Mobile Model, Payment Method, Brand

### 2. MTD Report
- KPI cards and slicers (Year / Quarter / Month / Day, Mobile Model, Payment Method)
- Line chart of **Month-to-Date (MTD)** sales

### 3. Same Period Last Year
- Compares **Total Sales vs. Same Period Last Year**
- Table and clustered column charts by Year, Quarter and Month

A page navigator is included on every page for easy movement between reports.

---

## 🗂️ Data Model

| Table | Description |
|---|---|
| `Sales_Data` | Fact table with transaction-level sales data |
| `Custom_Calender` | Date table (Year, Quarter, Month, Day, Day Name) used for time intelligence |

**Columns in `Sales_Data`:** Transaction ID, Date, Brand, Mobile Model, Units Sold, Price Per Unit, Customer Name, Customer Age, City, Payment Method, Customer Ratings, Rating_Status

---

## 🧮 DAX Measures

```DAX
Total_Quantity = SUM(Sales_Data[Units Sold])

Total_Sales = SUMX(Sales_Data, Sales_Data[Units Sold] * Sales_Data[Price Per Unit])

Transaction = COUNTROWS(Sales_Data)

Average_Price = AVERAGE(Sales_Data[Price Per Unit])

MTD = TOTALMTD([Total_Sales], Custom_Calender[Date].[Date])

QTD = TOTALQTD([Total_Sales], Custom_Calender[Date].[Date])

YTD = TOTALYTD([Total_Sales], Custom_Calender[Date].[Date])

Same Period Last Year = CALCULATE([Total_Sales], SAMEPERIODLASTYEAR(Custom_Calender[Date].[Date]))
```

---

## 🛠️ Tools & Skills Used

- **Power BI Desktop**
- **DAX** (measures and time intelligence)
- **Data modelling** (fact table + calendar table, relationships)
- **Data visualisation** and dashboard design (slicers, map, funnel, KPI cards, navigation)

---

## 🚀 How to Use

1. Clone or download this repository
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   ```
2. Open `Mobile_Sales_Dashboard.pbix` in **Power BI Desktop**
3. Use the slicers and page navigator to explore the report

> Power BI Desktop is free to download from Microsoft.

---

## 🖼️ Screenshots

Add your screenshots to a `screenshots/` folder and link them here:

```md
![Dashboard](screenshots/dashboard.png)
![MTD Report](screenshots/mtd_report.png)
![Same Period Last Year](screenshots/sply.png)
```

---

## 🔑 Key Insights

_Add your own findings here after exploring the dashboard, for example:_

- Top-performing brand and model
- City with the highest sales
- Most-used payment method
- Sales trend vs. last year

---

## 📁 Repository Structure

```
├── Mobile_Sales_Dashboard.pbix
├── screenshots/
└── README.md
```

---

## 👤 Author
**Saddam Pathan**

---

⭐ If you found this project useful, consider giving it a star!
