# Finance Data Projects

A collection of finance-focused data analysis projects, built to apply data and analytical skills to real-world financial questions.

## Projects

### 1. SQL Financial Data Analysis

Using SQL to analyze transaction-level financial data and uncover trends in revenue, customer behavior, and spending patterns.

**Dataset:** Online Retail Dataset (UK-based e-commerce transactions, ~500k rows)

**Key findings:**
- Top customer (ID 17450) generated over £187,000 in total revenue
- Revenue grew steadily from June to November 2011, peaking at £1.46M in November — likely seasonal demand ahead of the holiday period
- Revenue is heavily concentrated in the UK, indicating geographic concentration risk
- Average order value across all transactions: £376.36
- 1,454 customers had not purchased in over 90 days relative to the dataset's latest date, flagging them as at risk of churn

**Queries:**

```sql
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
```

**Status:** Complete

---

More projects coming soon, including dashboarding and financial modeling work.

