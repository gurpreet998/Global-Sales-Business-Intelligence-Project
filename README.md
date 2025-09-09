# End-to-End Global Sales Dashboard | Excel (EDA) + Power BI (ETL, Data Cleaning, Visualization)

## 📌 Project Overview  
This project showcases a **Global Sales Analytics Dashboard** built using **Excel (EDA)** and **Power BI (ETL, Modeling, Visualization)**.

The objective was to design a **multi-page interactive dashboard** that provides insights into sales, profitability, customer demographics, and product performance across regions.  

Business stakeholders can use this dashboard to track **KPIs, trends, targets vs actuals, and YOY performance**, helping them make **data-driven strategic decisions**.

---

## 🧭 Project Roadmap  

1. **Exploratory Data Analysis (EDA) – Excel**  
2. **ETL (Extract, Transform, Load) – Power BI Power Query**  
3. **Data Cleaning & Transformation**  
4. **Data Modeling**  
5. **Data Visualization (Multi-Page Dashboard)**
6. **Navigation Design**

---

## 🔍 Exploratory Data Analysis (EDA) – Excel  

Performed initial assumptions and calculated key metrics:  
- Since **Cost Price** was not provided, assumed it as **70% of Sales Price**.  
- Generated a **Targets Table** (quarterly and regional targets).  
- Calculated derived metrics:  
  - **Revenue** = Quantity × Sales Price  
  - **COGS** = 70% of Sales Price  
  - **Profit** = Revenue – COGS  
  - **Profit %** = Profit ÷ Revenue × 100  

---

## ⚙️ ETL & Data Cleaning – Power BI  

Steps performed in **Power Query**:  

1. **Loaded Data & Checked Data Types**  
   - Converted `Order Date` into **Date format (dd-mm-yyyy)** using locale.  
   - Ensured numeric columns (Sales Price, Quantity, Shipping Charges) are correctly set to **Decimal/Whole numbers**.  

2. **Trimmed & Cleaned Text Columns**  
   - Standardized values in fields like `Order Location` & `Product Category`.  

3. **Created Custom Columns**  
   - **YearQuarter** →  
     ```powerquery
     "Q" & Text.From(Date.QuarterOfYear([Order Date])) & "-" & Text.From(Date.Year([Order Date]))
     ```
   - **RegionQuarterYear** (for mapping targets with sales).  

4. **Target Table Adjustments**  
   - Added a **Region | Quarter-Year** column to ensure proper mapping with sales data.  

5. **Custom Calendar Table**  
   - Created using a **Blank Query**:  
     ```powerbi
     Custom Calendar = List.Dates(#date(2023,1,1),731,#duration(1,0,0,0))
     ```  
   - Added **Year, Quarter, Month columns** for time intelligence.  

6. **Location Mapping**  
   - Created a **Geo Table** with Latitude & Longitude for cities/regions.  

---

## 🗂️ Data Modeling  

- **Relationships Created**:  
  - `Sales[RegionQuarterYear]` (Many) → `Targets[RegionQuarterYear]` (One)  
  - `Sales[Order Date]`(Many) → `Custom Calendar[Date]`(One)
  - `Sales[Order Location]`(Many) → `City Mapping[Country]`(One)
  - Measure Table (for creating measures exclusively) not a part of model design

- **Star Schema Approach** adopted for simplicity:  
  - **Fact Table**: Sales  
  - **Dimension Tables**: Custom Calendar, Targets, City Mapping  

---

## 📊 Dashboard Pages & Visualizations  

### 1️⃣ Executive Overview  
**Focus**: High-level performance metrics.  
**Visuals Used**:  
- KPI Cards → Total Revenue, Profit, Orders, Profit Margin %  
- Clustered Column Chart → Quarterly Revenue vs Targets  
- Line Chart → Profit Trend  
- Donut Chart → Revenue by Product Category  
- Map → Revenue by Region  
- **Slicers** → Product, Year, Region  

👉 Gives executives a **quick health check** of overall business performance.  

![Executive Overview Dashboard](images/executive_overview.png)

---

### 2️⃣ Regional Performance  
**Focus**: Sales by region, demographics, and shipping.  
**Visuals Used**:  
- KPI Cards → Top/Bottom Regions by Revenue, Profit, Orders  
- Treemap → Top 5 Regions by Revenue  
- Bar Chart → Revenue by Age Buckets (18–23, 24–29, 30–35)  
- Donut → Revenue by Gender  
- Pie Chart → Profit by Shipping Type  

👉 Highlights **best/worst performing regions** and **customer segment contributions**.  

---

### 3️⃣ Product Insights  
**Focus**: Product-level performance.  
**Visuals Used**:  
- KPI Cards → Top/Bottom Products by Revenue, Profit, Orders  
- Bar Chart → Revenue by Product Category  
- Donut Chart → Orders by Product Category  
- Stacked Area Chart → Profit Margin % by Shipping Type  

👉 Helps identify **profitable products & categories**, as well as **shipping cost impact**.  

---

### 4️⃣ Trend Analysis  
**Focus**: Sales & Profit trends over time.  
**Visuals Used**:  
- KPI Cards → YOY % Change (Revenue, Profit, Orders, AOV)  
- Line Chart → Monthly Revenue Trend (with YOY comparison)  
- Line Chart → Monthly Profit Trend  
- Matrix → Product performance with Revenue, Profit, Margin, YOY % Change  

👉 Tracks **growth trends, seasonality, and product-level YOY performance**.  

---

### 🔄 Navigation Design  
To improve user experience, I designed a **custom navigation bar** available on all pages.  

- Added **buttons** for moving across different pages (Executive Overview, Regional Performance, Product Insights, Trend Analysis).  
- Created **icons (Home, Globe, Products, Chart, etc.)** for intuitive navigation.  
- Configured button actions with **page navigation** so users can easily move back and forth between sections.  
- Ensures the dashboard feels like a **cohesive application**, not just separate pages.  

---

## 🚀 Key Insights  

- Revenue growth concentrated in a few **top-performing regions**.  
- **Profit margins vary significantly** by shipping method.  
- Younger customers (18–23) generated **higher orders** but lower AOV.  
- Certain product categories consistently underperform, impacting profitability.  
- Clear **seasonality trends** detected in sales.  

---

## 📂 Repository Structure 

Global-Sales-Business-Intelligence-Project/
│── data/ # datasets
│── dashboard/ # Power BI .pbix file
│── images/ # Screenshots of dashboard pages
│── README.md # Project documentation


---

## 🛠️ Tools & Technologies  

- **Excel** → Exploratory Data Analysis (EDA)  
- **Power BI** → ETL, Modeling, Visualization  
- **DAX** → KPIs & YOY calculations  
- **Power Query** → Data transformation

## 📫 Let's Connect
If you're looking for a Data Analyst with a proven record of transforming data into insights and driving tangible business impact — I'd love to connect.

✉️ Email: gs268197@gmail.com

📱 Mobile: +91 7018320090

🔗 LinkedIn: linkedin.com/in/gurpreetsingh1998

💻 GitHub: github.com/gurpreet998

🌐 Portfolio: gurpreet-singh-998.vercel.app




