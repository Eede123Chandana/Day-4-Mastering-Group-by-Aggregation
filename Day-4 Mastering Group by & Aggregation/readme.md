# 📊 Mastering SQL GROUP BY & Aggregation

## 🎯 Overview

SQL `GROUP BY` and aggregate functions help summarize large datasets into meaningful information.

These concepts are essential for business reporting, customer segmentation, sales analysis, and performance monitoring.

**Objective:** Understand how to group records, apply aggregate functions, filter grouped results, and solve practical business problems using SQL.

---

## 1️⃣ What is GROUP BY?

`GROUP BY` combines rows sharing the same values into groups.

It is commonly used with aggregate functions to calculate totals, averages, counts, minimums, and maximums.

### Sample Dataset: Orders

| Category | Region | Sales |
|---|---|---:|
| Electronics | East | 120000 |
| Electronics | West | 90000 |
| Clothing | East | 45000 |
| Clothing | West | 30000 |
| Grocery | East | 25000 |
| Grocery | West | 35000 |

### SQL Query

```sql
SELECT
    category,
    SUM(sales) AS total_sales
FROM orders
GROUP BY category;
```

### Output

| Category | Total Sales |
|---|---:|
| Electronics | 210000 |
| Clothing | 75000 |
| Grocery | 60000 |

**Explanation:** Rows belonging to the same category are grouped, and their sales values are added together.

---

## 2️⃣ Why Aggregation Matters

Aggregation helps businesses:

- Summarize large transaction datasets.
- Compare performance across regions and categories.
- Calculate key business metrics.
- Identify trends and performance gaps.
- Generate meaningful reports and dashboards.

**Example:** A retail company can identify its highest-revenue product category without examining every transaction individually.

---

## 3️⃣ Aggregate Functions

| Function | Description | Business Application |
|---|---|---|
| COUNT() | Counts rows or non-NULL values | Total orders |
| SUM() | Calculates total | Total revenue |
| AVG() | Calculates average | Average salary |
| MIN() | Finds smallest value | Lowest transaction |
| MAX() | Finds largest value | Highest transaction |

### COUNT()

```sql
SELECT COUNT(*) AS total_orders
FROM orders;
```

**Note:** `COUNT(*)` counts all rows, while `COUNT(column)` excludes NULL values.

### SUM()

```sql
SELECT SUM(sales) AS revenue
FROM orders;
```

### AVG()

```sql
SELECT AVG(sales) AS avg_sales
FROM orders;
```

### MIN() and MAX()

```sql
SELECT
    MIN(sales) AS minimum_sale,
    MAX(sales) AS maximum_sale
FROM orders;
```

---

## 4️⃣ GROUP BY with Multiple Columns

SQL supports grouping by multiple attributes.

```sql
SELECT
    category,
    region,
    SUM(sales) AS total_sales
FROM orders
GROUP BY category, region;
```

**Use Case:** Compare category-wise sales across different regions.

Each unique combination of category and region forms a separate group.

---

## 5️⃣ WHERE vs HAVING

| WHERE | HAVING |
|---|---|
| Filters individual rows | Filters aggregated groups |
| Applied before grouping | Applied after grouping |
| Used for row-level conditions | Used for aggregate conditions |

### WHERE Example

Retrieve sales totals by category using transactions above 30,000.

```sql
SELECT
    category,
    SUM(sales) AS total_sales
FROM orders
WHERE sales > 30000
GROUP BY category;
```

### HAVING Example

Retrieve categories generating total sales above 70,000.

```sql
SELECT
    category,
    SUM(sales) AS total_sales
FROM orders
GROUP BY category
HAVING SUM(sales) > 70000;
```

### Combining WHERE and HAVING

```sql
SELECT
    category,
    SUM(sales) AS total_sales
FROM orders
WHERE region = 'East'
GROUP BY category
HAVING SUM(sales) > 50000;
```

**Explanation:**

1. WHERE selects records from the East region.
2. GROUP BY groups records by category.
3. SUM calculates category-wise revenue.
4. HAVING filters categories exceeding 50,000.

---

## 6️⃣ GROUP BY with ORDER BY

```sql
SELECT
    category,
    SUM(sales) AS total_sales
FROM orders
GROUP BY category
ORDER BY total_sales DESC;
```

**Business Use Case:** Rank product categories by revenue.

---

## 7️⃣ Real-World Business Applications

### 🛒 Retail – Total Sales by Region

```sql
SELECT
    region,
    SUM(sales) AS total_sales
FROM orders
GROUP BY region;
```

### 🏢 HR – Average Salary by Department

```sql
SELECT
    department,
    AVG(salary) AS avg_salary
FROM employees
GROUP BY department;
```

### 👥 Customer Analytics – Customers by City

```sql
SELECT
    city,
    COUNT(*) AS total_customers
FROM customers
GROUP BY city;
```

*Assumes one record per customer.*

### 📈 Sales – Highest Revenue Category

```sql
SELECT
    category,
    SUM(sales) AS revenue
FROM orders
GROUP BY category
ORDER BY revenue DESC
LIMIT 1;
```

### 📅 Operations – Monthly Orders

```sql
SELECT
    YEAR(order_date) AS year,
    MONTH(order_date) AS month,
    COUNT(*) AS total_orders
FROM orders
GROUP BY YEAR(order_date), MONTH(order_date)
ORDER BY year, month;
```

*Examples use MySQL syntax.*

---

## 8️⃣ Important SQL Rules

✅ Every selected non-aggregated column should appear in GROUP BY or be functionally dependent on grouped columns.

✅ WHERE filters rows before aggregation.

✅ HAVING filters aggregated results.

✅ COUNT(*) includes rows containing NULL values.

✅ COUNT(column), SUM(), AVG(), MIN(), and MAX() ignore NULL values in their input.

✅ GROUP BY can use multiple columns.

✅ ORDER BY sorts aggregated results.

✅ Aggregate functions can be combined in a single query.

---

## 9️⃣ Interview Questions

**Q1. What is GROUP BY?**

Groups records sharing common values for aggregation.

**Q2. GROUP BY vs ORDER BY?**

GROUP BY creates groups; ORDER BY sorts results.

**Q3. WHERE vs HAVING?**

WHERE filters rows; HAVING filters grouped results.

**Q4. COUNT(*) vs COUNT(column)?**

COUNT(*) counts all rows; COUNT(column) counts non-NULL values.

**Q5. Can GROUP BY use multiple columns?**

Yes. Each unique combination of grouped values forms a group.

---

## 🎯 Key Takeaways

- GROUP BY creates meaningful data summaries.
- Aggregate functions calculate business metrics.
- WHERE and HAVING control filtering at different stages.
- Multiple-column grouping enables detailed analysis.
- ORDER BY helps rank aggregated results.
- Aggregation is fundamental to SQL-based reporting.

---

## 💡 Final Thoughts

**GROUP BY and aggregation bridge the gap between raw transactional data and actionable business intelligence.**

They help analysts summarize data, measure performance, identify trends, and support informed business decisions.

### 🏷️ Topics

`SQL` `GROUP BY` `Aggregation` `COUNT` `SUM` `AVG` `MIN` `MAX` `HAVING` `MySQL` `Data Analytics` `Business Analytics`
