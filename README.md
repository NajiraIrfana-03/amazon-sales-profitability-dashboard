# Amazon Sales & Profitability Intelligence Dashboard

An interactive 3-page Business Intelligence dashboard built in **Microsoft Power BI**. It analyses e-commerce sales, profitability, customer behaviour, product performance, regional trends, returns and short-term sales forecasts across **Jan 2023 – Dec 2025**.

> **Note:** This is an independent educational portfolio project. The data is **synthetic sample data** created for learning. It is not official Amazon data, and the project is not affiliated with or endorsed by Amazon.

---

## Project Objectives

- Track overall sales, profit and profit margin.
- Measure sales target achievement and year-over-year growth.
- Identify top-performing products and high-value customers.
- Understand customer retention and repeat purchase behaviour.
- Compare regional sales and profitability.
- Monitor returns, refund amounts and return reasons.
- Explore future sales trends using Power BI forecasting.

---

## Tools & Technologies

| Tool | Used for |
|---|---|
| Microsoft Power BI Desktop | Data modelling, dashboards, visualisation |
| Power Query | Data cleaning and transformation |
| DAX | Measures, KPIs and time-intelligence calculations |
| CSV files | Data source |

---

## Repository Structure

| Folder / File | Contents |
|---|---|
| `Dataset` | The 7 source CSV files |
| `PowerBI` | The Power BI project file (`.pbix`) |
| `Dashboard-Screenshots` | Screenshots of the 3 dashboard pages |
| `Documentation` | Project documentation |
| `README.md` | Project overview |

---

## Dataset

Seven synthetic CSV files covering **Jan 2023 – Dec 2025**, available in the `Dataset` folder:

| Table | Type | Description | Size |
|---|---|---|---|
| Sales | Fact | Order lines with quantity, price, discount, sales, cost, profit, status, channel | 100,000 rows |
| Returns | Fact | Returned items with quantity, reason and refund amount | 7,963 rows (7,787 after cleaning) |
| Targets | Fact | Monthly sales and profit targets by region | 864 rows (24 regions x 36 months) |
| Customers | Dimension | Customer demographics and segment | 8,000 rows |
| Products | Dimension | Category, sub-category, brand, price and cost | 800 rows |
| Regions | Dimension | 24 cities grouped into North, South, East and West | 24 rows |
| Calendar | Dimension | Date table (year, quarter, month, week) | 1,096 days |

---

## Data Cleaning (Power Query)

- Trimmed and standardised text values in **Category**, **SubCategory** and **CustomerSegment** (they contained trailing spaces and inconsistent casing, which created duplicate categories).
- Replaced blank **SalesChannel** values (389 rows) with `unknown`.
- Removed **176 returns dated after 31 Dec 2025**, because the sales data and Calendar end in Dec 2025. This keeps the return KPIs, trend chart and Year slicer consistent.
- Verified there are no orphan keys: every sale links to a valid customer, product and region.

---

## Data Model

Dimension tables (**Customers, Products, Regions, Calendar**) connect to fact tables (**Sales, Returns, Targets**), so slicers filter across all pages. Regions are linked on `RegionID`, because the `Region` name repeats across several cities.

---

## Dashboard Pages

### 1. Executive Sales & Business Performance
- KPIs: Total Sales, Total Profit, Total Orders, Total Customers, Profit Margin, Average Order Value, Sales Target Achievement, Latest Year YoY Growth
- Sales & profit performance overview (monthly)
- Regional sales performance and regional profitability
- Year-over-year sales growth analysis
- Sales target achievement by region
- Slicers: Category, Year, Region, Sales Channel

### 2. Product & Customer Intelligence
- KPIs: Total Products, Total Customers, Average Discount %, Repeat Customers, Repeat Purchase Rate, Average Customer Sales
- Top 10 best-selling products (with profit)
- Top 10 high-value customers by sales
- Top 10 customers by order frequency (ties broken by sales)
- Category-wise profitability
- Discount impact on product profitability (scatter plot)
- Slicers: Category, SubCategory, Region, Order Date, Customer Segment

### 3. Regional, Returns & Future Performance
- KPIs: Total Returns, Returned Orders, Returned Profit Impact, Total Refund Amount, Total Returned Quantity
- Regional sales vs target
- Returns by product category and by region
- Return reasons analysis
- Monthly return trend
- Sales forecast for the next 3 months (Power BI forecasting with confidence interval)
- Slicers: Category, Year, Region, Return Reason

---

## Key DAX Measures

`Total_Sales` · `Total_Profit` · `profit_margin %` · `Total_Order` · `Total_Customer` · `Average Order Value` · `Average Discount %` · `Average Customer Sales` · `YoY Sales Growth %` · `Latest Year YoY Growth %` · `Total Sales Target` · `Sales_Target Achievement %` · `Repeat Customers` · `Repeat Purchase Rate %` · `Product Sales Rank` · `Category Profit` · `Total Returns` · `Returned Orders` · `Total Returned Quantity` · `Total Refund Amount` · `Returned Profit Impact`

---

## Headline Results

All dashboard values were reconciled against the source CSV files.

| Metric | Value |
|---|---|
| Total Sales | 387.87M |
| Total Profit | 107.12M |
| Profit Margin | 27.62% |
| Total Orders | 78,065 |
| Total Customers | 7,999 |
| Average Order Value | 4.97K |
| YoY Sales Growth | +2.11% (2024), -1.67% (2025) |
| Total Returns / Refunds | 7,787 returns / 20.28M |

---

## Key Insights

- **Electronics** and **Home & Kitchen** generate roughly two-thirds of total sales, and Electronics also has the highest profit and the most returned units.
- **South** is the top region by sales (112.4M, about 29% of the total), while profit margin stays almost flat across all regions (27.59% to 27.65%).
- Sales grew **+2.11% in 2024** and then declined **-1.67% in 2025**. February 2025 was the weakest month (about 9.6M).
- Return reasons are spread almost evenly (about 16% to 17% each), so no single reason dominates.

---

## Limitations

- The dataset is synthetic, so results show how the dashboard works and do not reflect a real business.
- The sales targets are about 10x higher than actual sales, so overall target achievement is only about 9.84%. In a real project, the targets would be confirmed with the business owner.
- Almost every customer has more than one order, so the Repeat Purchase Rate is about 99.99%.
- `OrderID` is not unique across rows (78,065 distinct IDs across 100,000 rows), so "Total Orders" is calculated as a distinct count of `OrderID`.
- Sales figures include orders of every status, including Cancelled.
- The forecast is a statistical estimate from Power BI's built-in forecasting on sample data.

---

## How to Open

1. Download the `.pbix` file from the `PowerBI` folder.
2. Open it in **Power BI Desktop**.
3. Download the CSV files from the `Dataset` folder. If prompted, update the data source path to where you saved them.

---

## Author

**Najira Irfana M**  
B.Com (Computer Applications) | Aspiring Data Analyst
