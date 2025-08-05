# 🏡 House Market Overview Dashboard

The **House Market Overview Dashboard** is a comprehensive Power BI report that provides in-depth insights into the real estate market. Designed for property analysts, realtors, and housing policy stakeholders, this dashboard showcases trends in regional sales, pricing behavior, and property type comparisons.

---

## 🧩 Dashboard Overview

### 🔹 Page 1: Regional Price & Sales Performance
- **Median Sales Price Change by Region:**  
  Stacked Bar Chart displaying shifts in median sales prices across Jutland, Fyn & Islands, Zealand, and Bornholm.
- **Units Sold (Latest Yr & Qtr):**  
  KPI Card showing 77 units sold in the latest year and quarter.
- **12-Month Sales Volume:**  
  KPI Card displaying total sales of 13 billion over the past year.
- **YOY Sales Growth by Sales Type:**  
  Line Chart illustrating year-over-year sales growth by different sales types.
- **Offer Price vs Purchase Price:**  
  Scatter Plot showing strong positive correlation between offer and final purchase prices.

### 🔹 Page 2: Sales Performance
- **Sales by Region:**  
  Stacked Bar Chart indicating total sales with Zealand leading at 95B, followed by Jutland (8B), Fyn & Islands (1.5B), and Bornholm (0B).
- **Key Influencers or Top Segments:**  
  Highlights drivers of purchase price along with a detailed sales table from Jan 1992, including day-wise YTD sales.
- **Offer to SQM Ratio by Sales Type:**  
  Stacked Bar Chart showing pricing efficiency per square meter across:  
  - Regular Sale: 15K  
  - Other Sale: 14K  
  - Family Sale: 12K  
  - Auction: 11K
- **Average Price per SQM by Region:**  
  Donut Chart breaking down pricing:  
  - Zealand: 20.85K (35.6%)  
  - Fyn & Islands: 13.62K (23.25%)  
  - Jutland: 13.51K (23.06%)  
  - Bornholm: 10.6K (18.1%)

### 🔹 Page 3: Property Type Comparison
- **Avg Offer & Purchase Price by House Type** → Clustered Bar Chart  
  Compares the average offer and purchase prices across house types such as Farms, Apartments, Townhouses, Villas, and Summerhouses.
- **Avg Inflation / Interest / Yield by House Type** → Clustered Bar Chart  
  Shows how macroeconomic indicators like inflation, interest rate, and rental yield impact different property types.
- **Avg SQM & SQM Price by House Type** → Line & Stacked Column Chart  
  Displays the average area (in square meters) and corresponding price per SQM for each property type.

#### 🔎 Slicers Used:
- **Area**
- **City**
- **Sales Type**
- **Region**

These slicers allow dynamic filtering of all visuals on the page to enable deeper comparative insights across different segments.

---

## ✅ Key Visuals

| 📊 **Chart Type**         | 📝 **Visual Description**                                                                    |
|--------------------------|-----------------------------------------------------------------------------------------------|
| **Stacked Bar Chart**     | Median Sales Price Change, Sales by Region, Offer to SQM Ratio                               |
| **KPI Cards**             | Units Sold, 12-Month Sales                                                                   |
| **Line Charts**           | YOY Sales Growth, Avg SQM Price                                                              |
| **Scatter Plot**          | Offer Price vs Purchase Price                                                                |
| **Donut Chart**           | Average Price per SQM by Region                                                              |
| **Clustered Bar Charts**  | Avg Offer/Purchase by House Type, Avg Inflation/Interest/Yield by House Type                |
| **Line + Column Chart**   | Avg SQM & SQM Price by House Type                                                            |
| **Slicers**             | Filter visuals by **Area**, **City**, **Sales Type**, and **Region**                        |

---

## 📂 Data Sources

| File                   | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| `Housing Data.csv`     | CSV dataset containing house prices, regions, dates, sales, offer/purchase prices, etc. |
| `Housing Dashboard.pbix` | Power BI file with all charts, filters, and modeling logic.               |

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** – For data modeling and dashboard development  
- **Power Query Editor** – For data transformation and shaping  
- **DAX (Data Analysis Expressions)** – For creating KPIs and calculated fields  
- **CSV File** – Raw source data used in report  

---

## 📷 Dashboard Preview

Screenshots:  

- `dashboard-preview-1`  :
<img width="776" height="444" alt="dashboard-preview-one" src="https://github.com/user-attachments/assets/82ee62d8-7aef-4e09-822b-0fa976bfe0ca" />

- `dashboard-preview-2`:
<img width="776" height="444" alt="dashboard-preview-two" src="https://github.com/user-attachments/assets/128e48fe-c902-45cf-af98-a9c5dd092357" />
  
- `dashboard-preview-3` :
<img width="783" height="447" alt="dashboard-preview-three" src="https://github.com/user-attachments/assets/20877e05-ad6b-43e7-affe-7ec46ec97c88" />

Demo:

https://github.com/user-attachments/assets/22e7a9e2-3ae4-463c-98c5-4fd19ef18302




  

---

## 🚀 Usage

1. Clone or download the repository.  
2. Open the `.pbix` file using Power BI Desktop.  
3. Reconnect the data source if needed.  
4. Explore the pages using slicers (e.g., Region, House Type, Sale Type).  
5. Use insights for real estate trend analysis, pricing strategies, or regional forecasting.  

---

## 📌 Use Case Highlights

- Compare pricing efficiency by sales type and region  
- Identify house types with best ROI (e.g., SQM price vs size)  
- Track yearly trends in residential sales and pricing  
- Perform detailed exploratory analysis using KPIs, charts, and filters  

---

## ✅ Steps Followed

1. **Load Data**  
   Imported `house_market.csv` into Power BI Desktop.

2. **Transform Data in Power Query**  
   Enabled Column Distribution, Column Quality, and Column Profile.

3. **Profiling Based on Entire Dataset**  
   Changed profiling settings to evaluate full dataset (not just first 1000 rows).

4. **Validated Data Quality**  
   Verified there were no null or error values across columns.

---

## 📌 DAX Formulas with Description & Purpose

### 1️⃣ Age
Calculates the age of the property.  
`Age = ABS(YEAR(Housing[date (MM/DD/YYYY)].[Date]) - Housing[year_build])`

---

### 2️⃣ Offer Price
Estimates the original offer price before discount.  
`Offer Price = (100 * Housing[purchase_price]) / (100 - Housing[%_change_between_offer_and_purchase])`

---

### 3️⃣ Average Price SQM
Calculates average price per square meter.  
`Average Price SQM = AVERAGE(Housing[sqm_price])`

---

### 4️⃣ Last 12 Month Sales
Returns total sales over the past 12 months.  
```DAX
Last 12 Month Sales = 
CALCULATE(
    SUM(Housing[purchase_price]),
    DATESINPERIOD(
        Housing[date (MM/DD/YYYY)],
        MAX(Housing[date (MM/DD/YYYY)]),
        -12,
        MONTH
    )
)
```

---

### 5️⃣ Median Sales Price Change
% change in median price YoY.  
```DAX
VAR CurrMedianPrice = 
    MEDIANX(
        FILTER(
            Housing,
            YEAR(Housing[date (MM/DD/YYYY)].[Date]) = 
            YEAR(MAX(Housing[date (MM/DD/YYYY)].[Date]))
        ),
        Housing[purchase_price]
    )

VAR PreMedianPrice = 
    MEDIANX(
        FILTER(
            Housing,
            YEAR(Housing[date (MM/DD/YYYY)].[Date]) = 
            YEAR(MAX(Housing[date (MM/DD/YYYY)].[Date])) - 1
        ),
        Housing[purchase_price]
    )

RETURN
    IF(
        PreMedianPrice <> 0,
        (CurrMedianPrice - PreMedianPrice) / PreMedianPrice,
        BLANK()
    )
```

---

### 6️⃣ Offer to SQM Ratio
Offer price per square meter.  
`Offer to SQM Ration = DIVIDE(SUM(Housing[Offer Price]), SUM(Housing[sqm]))`

---

### 7️⃣ Sales by Region
Region-wise total sales.  
```DAX
Sales by Region = 
CALCULATE(
    SUM(Housing[purchase_price]),
    ALLEXCEPT(Housing, Housing[region])
)
```

---

### 8️⃣ Total YTD Sales
Year-to-date total sales.  
```DAX
TotalYTD Sales = 
TOTALYTD(
    SUM(Housing[purchase_price]),
    Housing[date (MM/DD/YYYY)].[Date]
)
```

---

### 9️⃣ Units Sold in Latest Year & Quarter
```DAX
Units sold in latest Year & Quarter = 
CALCULATE(
    DISTINCTCOUNT(Housing[house_id]),
    YEAR(Housing[date (MM/DD/YYYY)]) = YEAR(MAX(Housing[date (MM/DD/YYYY)])) &&
    QUARTER(Housing[date (MM/DD/YYYY)]) = QUARTER(MAX(Housing[date (MM/DD/YYYY)]))
)
```

---

### 🔟 YOY Sales Growth
```DAX
YOY_Sales_Growth = 
VAR CurrYearSales =
    CALCULATE(
        SUM(Housing[purchase_price]),
        YEAR(Housing[date (MM/DD/YYYY)]) = YEAR(MAX(Housing[date (MM/DD/YYYY)]))
    )

VAR PrevYearSales =
    CALCULATE(
        SUM(Housing[purchase_price]),
        YEAR(Housing[date (MM/DD/YYYY)]) = YEAR(MAX(Housing[date (MM/DD/YYYY)])) - 1
    )

RETURN
    IF(
        PrevYearSales <> 0,
        (CurrYearSales - PrevYearSales) / PrevYearSales,
        BLANK()
    )
```

