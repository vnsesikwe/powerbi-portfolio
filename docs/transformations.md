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
- Removed duplicate DealerIDs
- Trimmed and cleaned text columns

---

## 🔹 DimModel Transformations

- Promoted headers
- Changed data types:
  - ModelID → Whole Number
  - Brand → Text
  - Model → Text
  - Segment → Text
  - EngineSize → Decimal
  - Fuel → Text
  - Price → Whole Number
  - Profit → Whole Number
- Removed null Brand and Model values
- Standardized segment naming (SUV, Sedan, Hatchback, Pickup)

---

## 🔹 FactSales Transformations

- Promoted headers
- Changed data types:
  - SaleID → Whole Number
  - Date → Date
  - DealerID → Whole Number
  - ModelID → Whole Number
  - Quantity → Whole Number
  - TotalPrice → Whole Number
  - Total Profit → Whole Number
- Removed duplicate transaction records
- Filtered out Quantity ≤ 0
- Created Year and Month columns from Date (optional for reporting)

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

