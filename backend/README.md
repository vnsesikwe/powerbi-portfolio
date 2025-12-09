# Top Car Dealers – Sales Performance Dashboard (Power BI)

## 1. Project Overview

**Business Case**

We are sales analysts for a car dealership network operating in **Botswana** and **South Africa**.  
Management needs a **Sales Analysis Tool** to answer:

- How much **revenue and profit** are we generating?
- Which **countries, cities, dealers, brands and models** are performing best?
- Which factors **increase or decrease profit**?

This Power BI project delivers an interactive **Sales Dashboard** built on the *Top Cars Database – Africa* dataset.

---

## 2. Analysis Goals & Dashboard Deliverables

**Sales Dashboard – Main Questions**

1. **Present Revenue by Country (ZA / BW)**
2. **Identify Top 3 Cars Sold (by quantity)**
3. **Compare Profit vs Quantity Sold by Brand**
4. **Visualize Revenue and Sales by City and Dealer**
5. **Use Key Influencers to understand what drives Profit**

---

## 3. Data Model Documentation

### 3.1 Tables

The model uses **three tables** loaded from `Top Cars Database - Africa.xlsx`:

- `Dealers`
- `Models`
- `Sales`

### 3.2 Relationships

- `Dealers[DealerID]` **1 → many** `Sales[DealerID]`
- `Models[ModelID]` **1 → many** `Sales[ModelID]`

This gives a **star-schema** style model:

`Dealers` (dimension) → `Sales` (fact) ← `Models` (dimension)

---

## 4. Table Dictionary

### 4.1 Dealers

| Column      | Type    | Description                                          |
|------------|---------|------------------------------------------------------|
| `DealerID` | Whole   | Unique identifier of each dealer                     |
| `DealerName` | Text  | Dealer / car sales company name                      |
| `City`     | Text    | City where the dealer is located                     |
| `Country`  | Text    | Country of the dealer (Botswana, South Africa)       |

### 4.2 Models

| Column           | Type    | Description                                      |
|------------------|---------|--------------------------------------------------|
| `ModelID`        | Whole   | Unique identifier of each car model              |
| `Brand`          | Text    | Car brand (Toyota, BMW, Kia, etc.)              |
| `Model`          | Text    | Model name (Corolla, 3 Series, Rio, etc.)       |
| `Segment`        | Text    | Vehicle segment (Sedan, Hatchback, Pickup, SUV) |
| `EngineSize (L)` | Decimal | Engine size in litres                           |
| `Fuel`           | Text    | Fuel type (Petrol, Diesel)                      |
| `Price (USD)`    | Whole   | List/standard price per unit                    |
| `Profit (USD)`   | Whole   | Profit per unit (price – cost)                  |

### 4.3 Sales

| Column         | Type        | Description                                              |
|----------------|------------|----------------------------------------------------------|
| `SaleID`       | Whole      | Unique identifier of each sale transaction               |
| `Date`         | Date       | Transaction date                                         |
| `DealerID`     | Whole      | FK → `Dealers[DealerID]`                                 |
| `ModelID`      | Whole      | FK → `Models[ModelID]`                                   |
| `Quantity`     | Whole      | Number of units sold in the transaction                  |
| `TotalPrice`   | Whole      | Total revenue for the transaction (Quantity × Price)     |
| `Total Profit` | Whole      | Total profit for the transaction                        |

---

## 5. DAX Measures Pack

All measures are created in the **Sales** (and Models) tables.

```DAX
-- Core KPIs
Revenue = SUM ( Sales[TotalPrice] )

Profit = SUM ( Sales[Total Profit] )

Quantity Sold = SUM ( Sales[Quantity] )

-- Cards on top of the dashboard
Brand Count = DISTINCTCOUNT ( Models[Brand] )

Model Count = DISTINCTCOUNT ( Models[Model] )

-- Helper measures
Avg Profit per Sale = 
    DIVIDE ( [Profit], DISTINCTCOUNT ( Sales[SaleID] ) )

Avg Profit per Unit =
    DIVIDE ( [Profit], [Quantity Sold] )

Revenue by Country =
    [Revenue]      -- used with Country on the visual axis

Profit by Country =
    [Profit]

Qty Sold by Model =
    [Quantity Sold]

Revenue by City =
    [Revenue]

Revenue by Dealer =
    [Revenue]

Profit by Brand =
    [Profit]

