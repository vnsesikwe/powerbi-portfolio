# 🔄 Power Query Transformations – African Car Sales Project

This document outlines the data preparation steps performed in Power Query before loading into the Power BI model.

---

## ✅ Source

- File: `Top Cars Database - Africa.xlsx`
- Tables imported:
  - Dealers
  - Models
  - Sales

---

## 🔹 DimDealer Transformations

- Promoted first row as headers
- Changed data types:
  - DealerID → Whole Number
  - DealerName → Text
  - City → Text
  - Country → Text
  
---

## 🔹 DimModel Transformations

- Promoted headers
- Changed data types:
  - ModelID → Whole Number
  - Brand → Text
  - Model → Text
  - Segment → Text
  - EngineSize → Decimal (Change type with United States Locale tranformation)
  - Fuel → Text
  - Price → Whole Number
  - Profit → Whole Number

---

## 🔹 FactSales Transformations

- Promoted headers
- Changed data types:
  - SaleID → Whole Number
  - Date → Date
  - DealerID → Whole Number
  - ModelID → Whole Number
  - Quantity → Whole Number
  - TotalPrice → Decimal
  - Total Profit → Decimal
  - Enable "Column Quality" check
  - Filter New Values on Sale ID to remove empty rows

---

## ✅ Load Settings

- All tables loaded as:
  - Import Mode
  - Star schema structure enforced
- Relationships validated in Model View

---

✅ These transformations ensure:
- Clean relational joins
- Accurate DAX calculations
- High performance Power BI visuals

