# 🧮 DAX Measures – African Car Sales Dashboard

This document contains all core and supporting DAX measures used in the Power BI Sales Dashboard.

---

## 🔹 Core KPIs

```DAX
Total Revenue = 
SUM ( FactSales[TotalPrice] )

Total Profit = 
SUM ( FactSales[Total Profit] )

Total Quantity Sold = 
SUM ( FactSales[Quantity] )

