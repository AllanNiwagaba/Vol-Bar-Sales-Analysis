# Vol Bar Sales Analysis

- Vol Bar is a fictious business, but the data used is from a real business scenerio.
  
## Table of Content

- [Project Over view](#project-over-view)
- [Tools used](#tools-used)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Findings](#findings)
- [Recommendations](#recommendations)
  
## Project Over view

This project analyzes sales performance at Vol Bar, focusing on product-level insights, profitability, and time-based trends.

The goal is:
- To measure the Impact of Discount Days on sales.
- To  help the business make data-informed decisions about sales strategy and pricing.
![Dashboard](https://github.com/user-attachments/assets/ae97ba45-65ac-41a6-8a90-6562c21085c7)

[Vol Bar Report.xlsx](https://github.com/user-attachments/files/20638176/Vol.Bar.Report.xlsx)

## Data Source

- Datasets used are stored in a folder on a local computer.

## Tools used

- Excel Power query - Cleaning
- Power Pivot - Data modelling & DAX Calculations
- Pivot Tables - Creating reports

## Data Cleaning and Preparation

This process involves data extraction, cleaning, and transforming data to get ready for analysis.

#### Extraction, Transformation & Load (ETL)
- Extracted data from the Vol folder (on desktop) into Power query.
- Promoted headers & Removed un wanted columns
- Filtered out the Nulls
- Assigned the correct data types
- Loaded data into power pivot

#### Data Modelling

- Created relationships between the data tables by connecting Sales(Fact Table) to Products Pricelist, Productcategories, Calendar(dimensional tables).

- Calculated new columns:
- ```Sale Amount = Sales[Qty]*Sales[Unit Price]```
- ```COGs (Cost of Goods) =Sales[Qty]*Sales[Unit Cost]```
- ```Profit Margin =Sales[Sale Amount]-Sales[COGs]```
- ```Type of Sales =IF(OR(OR(RELATED('Calendar'[Day of the week])="Wed",RELATED('Calendar'[Day of the week]) = "Thu"), RELATED('Calendar'[Day of the week]) = "Fri"),"Discount Sale", "Non Discount Sale")```

## Exploratory Data Analysis

The EDA Involved exploring sales to answer the following questions.

- What is the total sales and revenue made for this period?
- What is the sales performance for different product categories?
- What is the performance of Discount Vs Non Discount days?
- What products are most profitable?
- What is the overall sales trend over the six months period?
- What are products are top sellers.
- What are the peak sales Periods
- What are the best selling days?

![Discount Vs Non Discount Sales](https://github.com/user-attachments/assets/e539d1e6-d395-4e3a-a1e8-55bfef9416ce)


![Revenue   Profitability](https://github.com/user-attachments/assets/291dc64a-df0c-4e82-95da-653ae002f7ef)

## Data Analysis

This section highlights some of the DAX calculations used:

- **Sales**
```Sale Qty:=SUM(Sales[Qty])```

- **Revenue**
```Revenue:=SUM(Sales[Sale Amount])```

- **Total Cost of Goods**
```Total Cogs:=SUM(Sales[COGs])```

- **Total Profit**
```Gross Profit:=SUM(Sales[Profit])```

- **% Profit**
```%Gross Profit:=DIVIDE([Gross Profit], [Revenue])```

- **Best Selling day**
```Best Selling day:=MAXX(TOPN(1,SUMMARIZE('Calendar','Calendar'[Day of the week],"Selling days",[Avg Sales Per day]),[Selling days]),'Calendar'[Day of the week])```

## Findings

- The bar made sales of 29,373 (total units) and overall total revenue of 106 million. There was a total of 3,420 transactions.
- Beers and Softs made the most Sales.
- More sales were made on Non-discount days (75%) compared to Discount days.
- Suspense Tots & Glasses and Rwenzori Mineral Water were the most profitable products making above 4 million in profit.
- Saturday and Sunday are the best days with sat making over 1.5million on average
- April, May and June were the peak months with over 5,000 units sold. Howver, April made the most Revenue of over 21 million.

## Recommendations

- Focus Promotions on hight Profit Margin Products like Suspenses Tots & Glasses to increase their sales and maximize profitability

#### Recommendations based on Discount Vs Non discount sales

- Use bundling instead of discounts (eg. Buy 2, get 1 free). to increase quantity without reducing unit price. This will help maintain percieved value while driving volume
- Promote Experiences like music, themed nights, loyaly programs not just prices.
- Reduce the frequency of discount days to make them feel like special days.
- Collect feedback to understand  why customers keep away on discount days. Their insights may reveal beyond just pricing (e.g. over crowding, poor customer service)

