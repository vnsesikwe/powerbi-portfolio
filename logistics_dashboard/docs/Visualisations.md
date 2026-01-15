# 📈 Dashboard Visualisations Logic

This document describes the construction logic behind each visual in the Logistics Performance Dashboard.

---

## 🔹 Orders by Status

- **Visual Type:** Donut Chart  
- **Fields Used:**
  - Status  
  - Invoice Number (Count)

---

## 🔹 Top 5 Clients Performance

- **Visual Type:** Stacked Bar Chart  
- **Measure:**
  ```DAX
  Count of Orders = COUNTROWS(factInvoices)

