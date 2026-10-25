# meridian-mart-tableau-dashboard
Tableau dashboard analyzing retail sales, profit, discounts and shipping performance across regions, segments and products

# Meridian Mart Retail Performance

**Tableau Capstone Project**

A two-page interactive Tableau dashboard that shows where a US retail chain makes and loses money, and what it should do about it.

## Project Overview

**The company.** Meridian Mart is a US-based premium retail superstore chain, founded in 2011 and headquartered in Denver, Colorado. It sells Furniture, Office Supplies and Technology to Consumer, Corporate and Home Office customers across four regions: Central, East, South and West.

**The business problem.** The commercial team keeps orders, products and regional sales in scattered spreadsheets. There is no single view of performance and reports do not agree. Because of this, leaders struggle to:

- See sales and profit by region, category and customer group
- Measure how discounting affects profit
- Flag loss-making products and sub-categories
- Check how well each shipping method works

The Chief Commercial Officer asked for a detailed analysis of the sales data and an interactive dashboard to guide decisions. She suspected heavy discounting, an unclear product mix and the lack of one dashboard were behind shrinking profit on several product lines.

**What the dashboard answers.** It has two pages:

| Page | What it shows |
|---|---|
| **Overview** | Key numbers, profit by state, sales and profit by region, customer group and category, and the sales trend over four years |
| **Deep-Dive** | Best and worst cities, loss-making products, discount impact and patterns, shipping methods, delivery time and top customers |

You can filter by **Year, Region and Segment**, and use an **Items to Show** parameter (5 to 20) to change how many cities, customers or products appear in the ranked views.

**Tools:** Tableau, Microsoft PowerPoint (for the findings presentation).

## Data

The data is the Meridian Mart sales dataset provided with the 10Alytics capstone: orders placed from **2022 to 2025** (ship dates run into 2026). As described in the data dictionary, each sales row links to location, customer and product details through ID fields.

**Key columns**

| Column | Description |
|---|---|
| Order ID, Order Date, Ship Date | Which order it is, when it was placed and when it shipped |
| Ship Mode | Shipping method (Same Day, First Class, Second Class, Standard Class) |
| Customer ID, Customer Name, Segment | Who bought: Consumer, Corporate or Home Office |
| Country/Region, City, State, Postal Code, Region | Where the order went (Central, East, South, West) |
| Product ID, Category, Sub-Category, Product Name | What was sold: Furniture, Office Supplies or Technology |
| Sales, Quantity | Revenue and number of units on each order line |
| Discount | Discount applied to the line (0 to 1) |
| Profit | Profit or loss on the line |

**Calculated fields and parameters**

| Field | Formula or purpose |
|---|---|
| Profit Margin | `SUM([Profit]) / SUM([Sales])` (dividing the totals, not averaging row by row) |
| Order Count | `COUNTD([Order ID])` (each order has several rows, so a plain count would be too high) |
| Delivery Days | `DATEDIFF('day', [Order Date], [Ship Date])` |
| Discount groups | 0%, 1-10%, 11-20%, 21-30% and 31%+ |
| Profit Status | Labels each product or group as "Profitable" or "Loss-Making" |
| Year-over-year change | 2025 compared with 2024, using LOD expressions |
| Items to Show | Parameter (5 to 20) that controls the top and bottom lists |

## Key Questions

1. **KPI Overview:** What are total sales, profit, margin and order count?
2. **Regional Split:** How do sales and profit compare by region and state?
3. **Top / Bottom Cities:** Which cities make the most and least profit?
4. **Customer Segments:** How do Consumer, Corporate and Home Office compare on sales and profit?
5. **Category Performance:** How do categories and sub-categories perform?
6. **Loss-Makers:** Which sub-categories or products lose money?
7. **Discount Impact:** How does the discount level affect profit, and where is the break-even point?
8. **Discount Patterns:** What is the average discount by region, category and segment?
9. **Sales Trend:** How have sales and profit changed month by month and year by year?
10. **Ship Mode Mix:** How are the shipping methods used, and what do they earn?
11. **Delivery Time:** How many days does delivery take by shipping method and region?
12. **Top Customers:** Who are the top customers by sales and by profit?

## Key Findings

1. **Profit fell in 2025.** Over four years the business made **$4,470,701** in sales and **$480,045** in profit from **2,100 orders** and **510 customers**. In 2025, sales were **$1,009,252 (17.0% lower than 2024)** and profit was **$119,837 (20.9% lower)**. Orders also fell 8.0%.

2. **Discounts above 30% lose money.** An average sale makes **$378.8** with no discount, only **$7.1** at 21 to 30% off, and loses **$403.3** above 30% off. Break-even is at about a 30% discount. Even so, the average discount is **20.7%**, and every region, category and segment sits between 16% and 26%, so discounting is spread widely rather than targeted.

3. **One product type carries the profit, and tables and machines lose money.** Copiers earn **$410,318, which is 85.5% of all profit**. Tables (**-$88,743**) and Machines (**-$36,495**) lose **$125,238** together. Four of the five biggest money-losing products are tables, led by the Hon Rectangular Table at **-$32,104**.

4. **Regions and customer groups keep different amounts of profit.** East makes **$175,032** profit on $1,272,520 of sales (about **$14 kept from every $100 sold**). West sells almost the same ($1,262,719) but makes only **$112,653** (about **$9 from every $100**). Colorado is the only state in loss on the map, and Denver, the head office city, lost **$4,510**. By customer group, Home Office keeps about $12 of every $100 sold, against about $10 for Consumer, which brings in 49.6% of all sales.

5. **Shipping choice sets the wait, and a few customers matter a lot.** Standard Class carries **58.8% of orders** and **57.0% of profit**, and takes about 5.5 days, against about 2.4 days for First Class. Regions differ by 0.3 days or less within each method. Three customers (Andrew Thomas, Emily Davis and Michelle Clark) are in both top-five lists and make **9.8% of all profit**.

> **Notes:** "About $X of every $100" is rounded. The best and worst lists show 5 items. Discount results are averages per sale, and the data shows what happened rather than proving why.

## Recommendations

1. **Limit discounts to 20%.** Ask for approval above 20% off and stop discounts above 30%, where the average sale loses money.
2. **Fix Tables and Machines.** Together they lost $125,238, about a quarter of today's profit. Review prices and costs, talk to suppliers, and drop or renegotiate the worst products.
3. **Do not depend only on Copiers.** They make 85.5% of profit. Protect their supply and pricing, and help weak sellers such as Storage ($6,791 profit on $203,034 of sales) earn more.
4. **Help the West earn more.** Compare discounting and costs with the East, and review Colorado and Denver, the only losses on the map.
5. **Grow Home Office and Corporate customers.** They keep more profit from each dollar than Consumer. Offer value rather than big discounts, and look after top customers.
6. **Watch profit every month.** Use the dashboard to track profit, discounts and money-losing products. Delivery times are steady across regions, so shipping needs no change.

<img width="1695" height="847" alt="Tableau Dashboard 2" src="https://github.com/user-attachments/assets/97f54184-3368-4211-96e9-052caf93f2fd" />
<img width="1682" height="830" alt="Tableau Dashbaord 1" src="https://github.com/user-attachments/assets/ec093d68-b805-476b-ac8d-eae3865bd677" />

