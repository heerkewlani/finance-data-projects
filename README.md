# Finance Data Projects

A collection of finance-focused data analysis projects, built to apply data and analytical skills to real-world financial questions.

## Projects

### 1. SQL Financial Data Analysis
Using SQL to analyze transaction-level financial data and uncover trends in revenue, customer behavior, and spending patterns.

-- Query 1: Top 10 customers by revenue
SELECT 
    CustomerID,
    SUM(Quantity * UnitPrice) AS TotalRevenue
FROM transactions
GROUP BY CustomerID
ORDER BY TotalRevenue DESC
LIMIT 10;

-- Query 2: Month-over-month revenue trend
SELECT 
    strftime('%Y-%m', InvoiceDate) AS Month,
    SUM(Quantity * UnitPrice) AS MonthlyRevenue
FROM transactions
GROUP BY Month
ORDER BY Month;

-- Query 3: Revenue by country
SELECT 
    Country,
    SUM(Quantity * UnitPrice) AS CountryRevenue
FROM transactions
GROUP BY Country
ORDER BY CountryRevenue DESC;

-- Query 4: Average order value
SELECT 
    AVG(InvoiceTotal) AS AvgOrderValue
FROM (
    SELECT 
        InvoiceNo,
        SUM(Quantity * UnitPrice) AS InvoiceTotal
    FROM transactions
    GROUP BY InvoiceNo
);

-- Query 5: Customers at risk of churn (no purchase in last 90 days of dataset)
SELECT 
    CustomerID,
    MAX(InvoiceDate) AS LastPurchaseDate,
    JULIANDAY((SELECT MAX(InvoiceDate) FROM transactions)) - JULIANDAY(MAX(InvoiceDate)) AS DaysSinceLastPurchase
FROM transactions
GROUP BY CustomerID
HAVING DaysSinceLastPurchase > 90
ORDER BY DaysSinceLastPurchase DESC;

