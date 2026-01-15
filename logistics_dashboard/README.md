
# 🚚 Power BI Portfolio – Logistics Performance Dashboard

**TopClass Freight Forwarder**

---

## 📌 Project Overview

This project is an end-to-end **Power BI Logistics Analytics Dashboard** developed for the fictional but realistic logistics company **TopClass Freight Forwarder**.
The dashboard analyzes the **overall situation of orders and their delivery conclusion status**, focusing on operational performance across **Botswana** and **South Africa**.

It is designed to support **project analysts and operations managers** in monitoring service quality, delivery efficiency, and client performance.

### ✅ Business Questions Answered

* How many orders are **On Time, Late, or Not Delivered**?
* Which are the **Top 5 clients** by order volume and service performance?
* Where do **late orders originate** geographically?
* How do **orders trend across the year**?

This solution is fully **portfolio-ready**, featuring:

* A structured **star-schema data model**
* Calculated **DAX columns and measures**
* A professional **Power BI dashboard**
* Clean **Power Query transformations**
* Clear **business-driven documentation**

---

## 🎯 Analysis Goals & Dashboard Deliverables

### Main Dashboard Objectives

1. Visualize the **number of orders by delivery status**
2. Analyze the **Top 5 clients’ performance** to inspect service quality
3. Identify the **origin of late orders**
4. Explain **order distribution across the year**

---

## 🧱 Data Model Architecture

The model follows a **Star Schema** design.

### Fact Table

**factInvoices**

* Carrier Code
* ClientCode
* Collection Date
* Contracted Term
* Delivery Date
* Expected Delivery Date
* Gross Weight (kg)
* Invoice Number
* Event

### Dimension Tables

**dimCarriers**

* Carrier
* Carrier Code
* Warehouse

**dimClients**

* ClientCode
* ClientName
* City
* Country

### Relationships (1 → Many)

* `dimCarriers[Carrier Code]` → `factInvoices[Carrier Code]`
* `dimClients[ClientCode]` → `factInvoices[ClientCode]`

This structure ensures:

* Accurate aggregation
* High model performance
* Clean filtering across all visuals

---

## 🧮 Calculated Columns & Measures

### Expected Delivery Date

```DAX
Expected Delivery Date =
factInvoices[Contracted Term] + factInvoices[Collection Date]
```

### Delivery Status

```DAX
Status =
IF(
    factInvoices[Delivery Date] > factInvoices[Expected Delivery Date],
    "Late",
    IF(
        ISBLANK(factInvoices[Delivery Date]),
        "Not Delivered",
        "On Time"
    )
)
```

### Count of Orders

```DAX
Count of Orders = COUNTROWS(factInvoices)
```

---

## 📊 Dashboard Visualisations

### 🔹 Orders by Status

* **Visual:** Donut Chart
* **Fields:** Status, Invoice Number (Count)

### 🔹 Top 5 Clients Performance

* **Visual:** Stacked Bar Chart
* **Fields:** ClientName, Count of Orders
* **Legend:** Status
* **Filter:** Top 5 Clients by Count of Orders

### 🔹 Origin of Late Orders

* **Visual:** Map
* **Fields:** Origin City, Count of Orders (Bubble size)
* **Filter:** Status = Late

### 🔹 Orders Across the Year

* **Visual:** Stacked Column Chart
* **Fields:** Invoice Date (X-axis), Count of Orders (Y-axis)

---

## 🧹 Power Query – Transformation Summary

### Carriers Details (PDF)

* Filter null rows in Column 1 and Column 4
* Delete Column 2 and Column 3
* Promote first row to headers
* Split Carrier field by delimiter: `space - space`
* Rename columns to **Carrier Code** and **Carrier**

### ClientsBase (CSV)

* Remove empty columns
* Load dataset

### Invoice Records (Excel)

* Remove promotional headers
* Change data types via Applied Steps
* Filter null Invoice Numbers
* Promote first row to headers



## 📚 Supporting Documentation

* 🧹 [Transformation Notes](docs/transformations.md)  
* 📈 [Visualisations Logic](docs/Visualisations.md)

These files provide deeper technical details on **data preparation and visual construction logic** used in the report.
