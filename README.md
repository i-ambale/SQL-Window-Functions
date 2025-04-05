# SQL Window Functions
© ExploreAI Academy  
By **Ibrahim Ambale** | [GitHub Profile](https://github.com/IbrahimAmbale)

## Overview

This notebook demonstrates the use of **SQL window functions** on a sample SQLite database (`Northwind.db`) for a retail company. It includes advanced calculations such as **ranking**, **running totals**, **moving averages**, and **differences in date fields**.

> ⚠️ This notebook is intended for local environments and will not run on Google Colab, as it requires access to the `Northwind.db` SQLite file.

## Learning Objectives

By the end of this notebook, you will be able to:

- Apply the `RANK()` function to rank rows within partitions.
- Calculate **running totals** using aggregate window functions.
- Use the `LAG()` function with `julianday()` (in SQLite) to compute differences between consecutive dates.
- Derive **moving averages** using window functions.

## Handling Date Differences in SQLite

SQLite does **not support** MySQL’s `TIMESTAMPDIFF()` function.  
To compute the difference between two dates in SQLite:

```sql
SELECT 
  CustomerID, 
  OrderDate, 
  LAG(OrderDate) OVER (PARTITION BY CustomerID ORDER BY OrderDate) AS PrevOrderDate,
  julianday(OrderDate) - julianday(LAG(OrderDate) OVER (PARTITION BY CustomerID ORDER BY OrderDate)) AS DaysBetween
FROM Orders;
```
This query calculates the number of days between each order and the previous one per customer using `julianday()`.
Getting Started
Clone this repository or download the notebook and Northwind.db file.

Ensure the database file is in the same folder as the notebook.

Open the notebook in Jupyter or VS Code and run each cell.

License & Attribution
This project is part of the ExploreAI Academy Data Science curriculum.
Developed by Ibrahim Ambale – GitHub: IbrahimAmbale. 
