# 🚗 Power BI Portfolio – African Car Sales Performance Dashboard

## 📌 Project Overview

This project is an end-to-end **Power BI Sales Analytics Dashboard** built using the fictional but realistic **“Top Cars Database – Africa”** dataset.  
The analysis focuses on vehicle sales across dealerships in **Botswana** and **South Africa**, designed to support **executive decision-making** through interactive analytics.

### ✅ Business Questions Answered:
- How much **revenue and profit** is the business generating?
- Which **countries, cities, dealers, brands, and models** perform best?
- Which **factors drive or reduce profitability**?
- How do **quantity sold and profit compare across brands**?

This solution is fully **portfolio-ready**, featuring:
- A clean **star schema data model**
- Professionally written **DAX measures**
- A well-structured **Power BI report**
- Clear **business insights & documentation**

---

## 🎯 Analysis Goals & Dashboard Deliverables

### Main Dashboard Objectives:
1. Present **Revenue by Country (Botswana vs South Africa)**
2. Identify **Top 3 Car Models Sold (by Quantity)**
3. Compare **Profit vs Quantity Sold by Brand**
4. Visualize **Revenue and Sales by City and Dealer**
5. Use **Key Influencers (Page 2)** to determine what drives **Profit**

---

## 🧱 Data Model Architecture

The model follows a **classic Star Schema** design for performance and scalability.

### Tables Used:
- **FactSales** (Sales Transactions)
- **DimDealer** (Dealership Information)
- **DimModel** (Vehicle Information)

### Relationships (1 → Many):
- `DimDealer[DealerID]` → `FactSales[DealerID]`
- `DimModel[ModelID]` → `FactSales[ModelID]`

This structure enables:
- High model performance  
- Clean filtering across visuals  
- Accurate aggregation for KPIs  

---

## 📘 Data Dictionary

### 🏢 DimDealer

| Column | Type | Description |
|--------|------|-------------|
| DealerID | Whole | Unique dealer identifier |
| DealerName | Text | Name of dealership |
| City | Text | Dealer city |
| Country | Text | Country (Botswana / South Africa) |

### 🚘 DimModel

| Column | Type | Description |
|--------|------|-------------|
| ModelID | Whole | Unique model identifier |
| Brand | Text | Vehicle brand |
| Model | Text | Vehicle model name |
| Segment | Text | Sedan, Hatchback, SUV, Pickup |
| EngineSize (L) | Decimal | Engine size |
| Fuel | Text | Petrol / Diesel |
| Price (USD) | Whole | Price per unit |
| Profit (USD) | Whole | Profit per unit |

### 📊 FactSales

| Column | Type | Description |
|--------|------|-------------|
| SaleID | Whole | Unique transaction ID |
| Date | Date | Transaction date |
| DealerID | Whole | FK → DimDealer |
| ModelID | Whole | FK → DimModel |
| Quantity | Whole | Units sold |
| TotalPrice | Whole | Quantity × Price |
| Total Profit | Whole | Quantity × Profit |

---

## 🧮 DAX Measures Pack

```DAX
-- Core KPIs
Total Revenue = SUM ( FactSales[TotalPrice] )
Total Profit = SUM ( FactSales[Total Profit] )
Total Quantity Sold = SUM ( FactSales[Quantity] )

-- Counts
Brand Count = DISTINCTCOUNT ( DimModel[Brand] )
Model Count = DISTINCTCOUNT ( DimModel[Model] )

-- Profitability
Profit Margin % = DIVIDE ( [Total Profit], [Total Revenue] )

-- Averages
Avg Profit per Sale =
DIVIDE ( [Total Profit], DISTINCTCOUNT ( FactSales[SaleID] ) )

Avg Profit per Unit =
DIVIDE ( [Total Profit], [Total Quantity Sold] )

-- Breakdown Measures
Revenue by Country = [Total Revenue]
Revenue by City = [Total Revenue]
Revenue by Dealer = [Total Revenue]
Profit by Brand = [Total Profit]
Quantity by Model = [Total Quantity Sold]
```


## 📚 Additional Documentation

Detailed technical documentation for this project is available below:

- 📘 [Table Dictionary](docs/table_dictionary.md)
- 🧮 [DAX Measures Reference](docs/DAX_measures.md)
- 🔄 [Power Query Transformations](docs/transformations.md)

These documents provide deeper insight into the **data structure, calculations, and data preparation logic** used in this project.
