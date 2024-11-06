# CAPSONE PROJECT

## Project Title: The Sales Performance Analysis for a Retail Store

## Project Summary
---
This project focuses on a detailed analysis of sales data for a retail store, aiming to deliver insights that can help the business optimize inventory, identify growth opportunities, and enhance customer satisfaction. By analyzing key metrics such as product sales, regional performance, and monthly trends, this project offers a comprehensive view of the store’s sales dynamics.

## Data Sources
---
The primary source of data used in this project is a stimulated sales data for a retail store.

CustomerID: Unique identifier for each customer.

CustomerName: Name of the customer

Product: Name of the product sold

Region: Geographic region of the sale (North, South, East, West)

Order Date: The date the product was ordered

Quantity: the number of units sold

Unit Price: the price per unit

## The Data Tools Used
---
•	Microsoft Excel: Excel was used for initial data exploration, cleaning, and basic analysis. Pivot tables and formulas were applied to calculate metrics like average sales 
  per product and total revenue by region.[Download here](http://www.microsoft.com)
  
•	SQL: SQL was employed to load and query the dataset within a SQL Server environment. This allowed for more advanced analysis, such as calculating total revenue per 
  product, identifying top-performing products, and analyzing sales trends. SQL also enabled efficient filtering and grouping to derive insights from large volumes of data.
  
•	Power BI: Power BI was used to create an interactive dashboard that visually represents the insights obtained from Excel and SQL analyses. The dashboard includes 
  components like a sales overview, top-performing products, and regional breakdowns, allowing stakeholders to interact with the data and quickly understand key findings.
  
•	Github for portfolio building

## Data Cleaning and Preparation
---
• Removing Duplicate: Eliminated duplicated records to ensure data accuracy  

• Creating New Calculated Columns: I added a new sales column to calculate the sum of unit price and quantity

• Pivot Tables: I created pivot tables to analyze sales by product, region, and period, total revenue by Product

• Excel functions (SUM, COUNT, AVERAGE, AVERAGEIF, AND SUMIF) for statistical calculations like total revenue, and average revenue.
## Exploratory Data Analysis
---
Exploratory data analysis invoved explorying the data to answer some of the question, needful for the data such as;
• What is the total sales for each product category. 

• What is the number of sales transactions in each region. 

• Calculate the highest-selling product by total sales value.

• Calculate the total revenue per product. 

• Calculate  the monthly sales totals for the current year. 

• Find the top 5 customers by total purchase amount. 

• Calculate the percentage of total sales contributed by each region. 

• Identify products with no sales in the last quarteR

## Data Analysis 
---
This is where I include some basic lines of codes or queries uesd during the analysis;

```SQL
Select * from [dbo].[SalesData]
```

SELECT Product,SUM(Quantity*unitprice) as TotalSales
FROM [dbo].[SalesData]
GROUP BY Product;

SELECT Region, COUNT(*) AS SalesTransactions
FROM [dbo].[SalesData]
GROUP BY Region;

SELECT Top 1 product, sum(quantity * unitprice) as TotalSales
FROM [dbo].[SalesData]
GROUP BY Product
ORDER BY TotalSales DESC;

SELECT product, sum(quantity * unitprice) as TotalRevenue
FROM [dbo].[SalesData]
GROUP BY Product;

SELECT MONTH(OrderDate) AS Month, Sum (quantity * unitprice) as MonthlySales
FROM [dbo].[SalesData]
WHERE YEAR(OrderDate) = YEAR(GETDATE())
GROUP BY MONTH(OrderDate)
ORDER BY MONTH;

SELECT Top 5 Customer_Id, Sum (quantity * unitprice) as TotalPurchaseAmount
FROM [dbo].[SalesData]
GROUP BY Customer_Id
ORDER BY TotalPurchaseAmount DESC;

SELECT Region, 
SUM (Sales) AS TotalSales, 
ROUND((SUM(Sales) * 100 / (SELECT SUM(Sales)
FROM[dbo].[SalesData] )), 2) AS SalesPercentage
FROM[dbo].[SalesData]
GROUP BY Region;

SELECT Product
FROM [dbo].[SalesData]
WHERE Product NOT IN (
SELECT DISTINCT Product
FROM [dbo].[SalesData]
WHERE OrderDate >= DATEADD(MONTH, -1, GETDAT)
GROUP BY Product;

## The Sales Data Pivot Table Analysis
![image](https://github.com/user-attachments/assets/62f70d99-5bf6-46c9-90cc-f7ea254a6f2f)


