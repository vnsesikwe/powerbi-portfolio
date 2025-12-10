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

Brand Count = 
DISTINCTCOUNT ( DimModel[Brand] )

Model Count = 
DISTINCTCOUNT ( DimModel[Model] )

Profit Margin % = 
DIVIDE ( [Total Profit], [Total Revenue] )

Avg Profit per Sale =
DIVIDE ( 
    [Total Profit], 
    DISTINCTCOUNT ( FactSales[SaleID] ) 
)

Avg Profit per Unit =
DIVIDE ( 
    [Total Profit], 
    [Total Quantity Sold] 
)

Revenue by Country = [Total Revenue]
Revenue by City = [Total Revenue]
Revenue by Dealer = [Total Revenue]

Profit by Brand = [Total Profit]

Quantity by Model = [Total Quantity Sold]
