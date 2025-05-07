Power BI Sales Performance Dashboard – Adventure Works

This Power BI dashboard analyzes the sales performance of Adventure Works across regions, time, and product categories. It was built to practice key Power BI features like data modeling, DAX, bookmarks, slicers, and dynamic visuals.


Key Insights

1. Total Sales Under Target  
   Total sales reached around $2.97bn, which is significantly below the corporate sales target of $7bn.

2. Europe Leads in Sales Volume  
   Europe emerged as the top-performing region with $3.5bn in total sales, followed closely by Australia at $3.2bn.

3. Strong Category Profit Margins  
   Categories like Clothing, Bikes, and Accessories show consistently strong margin percentages—hovering near 100% —indicating high profitability in these lines.

4. North America Lags Behind  
   Despite being a major region, North America contributed only $0.8bn, suggesting potential growth opportunities or underlying sales issues in that market.

5. Sales Spiked Then Plateaued  
   From 2020 to 2021, sales nearly doubled, indicating strong market performance. However, the minimal increase from 2021 to 2022 shows sales momentum may be slowing.

6. High Margins Suggest a Volume Strategy  
   Since margins are high across all product categories, strategic focus should shift to increasing sales volume rather than improving unit profitability.



Dashboard Preview

[Overview Screenshot](Images/overview.png)

Tools & Features Used

- Power BI Desktop
- DAX Measures
- Time Intelligence
- Bookmarks
- KPI Cards
- Slicers & Drill-through
- Custom formatting & tooltips

DAX Formula 

- (YoY Growth)
YoY % Growth = 
VAR CurrentSales = [Total Sales]
VAR PreviousSales = CALCULATE([Total Sales], DATEADD('Order Date'[Date], -1, YEAR))
RETURN 
    DIVIDE(CurrentSales - PreviousSales, PreviousSales)

- Total Sales
Total Sales = SUM (Sales[Line Total Sales])

- Total Sales (Calculated with SUMX)
Total Sales SUMX = SUMX(Sales, (Sales[Unit Price] * Sales[Order Quantity]) )

- Cumulative Year-to-Date (YTD) sales 
YTD Sales = TOTALYTD([Total Sales], 'Order Date'[Order Date])

- Previous Year Total Sales (PY Total Sales)
PY Total Sales = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Order Date'[Order Date]))
