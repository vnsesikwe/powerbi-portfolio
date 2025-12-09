
---

# ✅ 2. `docs/table_dictionary.md`

```md
# 📘 Table Dictionary – African Car Sales Dataset

This document defines all tables and fields used in the Power BI data model.

---

## 🏢 DimDealer

| Column | Type | Description |
|--------|------|-------------|
| DealerID | Whole | Unique identifier for each dealer |
| DealerName | Text | Name of dealership |
| City | Text | Dealer city |
| Country | Text | Dealer country (Botswana / South Africa) |

---

## 🚘 DimModel

| Column | Type | Description |
|--------|------|-------------|
| ModelID | Whole | Unique identifier for each car model |
| Brand | Text | Car manufacturer |
| Model | Text | Model name |
| Segment | Text | Vehicle type (SUV, Sedan, Hatchback, Pickup) |
| EngineSize (L) | Decimal | Engine displacement |
| Fuel | Text | Fuel type (Petrol, Diesel) |
| Price (USD) | Whole | Unit selling price |
| Profit (USD) | Whole | Unit profit |

---

## 📊 FactSales

| Column | Type | Description |
|--------|------|-------------|
| SaleID | Whole | Unique transaction identifier |
| Date | Date | Sales transaction date |
| DealerID | Whole | FK → DimDealer |
| ModelID | Whole | FK → DimModel |
| Quantity | Whole | Units sold |
| TotalPrice | Whole | Quantity × Price |
| Total Profit | Whole | Quantity × Profit |

---

✅ This table dictionary supports:
- Data governance  
- Data modeling validation  
- Stakeholder documentation  
- Portfolio inspection  

