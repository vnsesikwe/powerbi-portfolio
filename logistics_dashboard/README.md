Excellent. Below is the **final, clean GitHub documentation structure** with the **Data Model section inserted directly into the README** and the remaining content split into **supporting markdown files**.

You can copy each file block directly into GitHub.

---

# 📁 Repository Structure

```
logistics-dashboard/
│
├── data/
│   ├── ClientsBase.csv
│   ├── Invoices.csv
│   ├── Invoice Records 2021-2022.xlsx
│   ├── Carriers Details.pdf
│
├── dashboard/
│   └── Logistics Dashboard.pbix
│
├── docs/
│   ├── Data_Cleaning_Notes.md
│   ├── Visualisations.md
│
├── images/
│   ├── dashboard_overview.png
│   └── model_view.png
│
└── README.md
```

---

# 📄 README.md

```md
# 📦 Logistics Dashboard – TopClass Freight Forwarder

## 📌 Project Overview
This project delivers a Data Analysis Dashboard for TopClass Freight Forwarder, built to analyze the overall situation of orders and their conclusion status.

---

## 🎯 Project Goals
- Analyze overall order performance
- Monitor order completion and delays
- Support operational decision-making

---

## 🧱 Data Model (Star Schema)

### Fact Table – factInvoices
- Carrier Code  
- ClientCode  
- Collection Date  
- Contracted Term  
- Delivery Date  
- Expected Delivery Date  
- Gross Weight (kg)  
- Invoice Number  
- Event  

### Dimension Tables

**dimCarriers**
- Carrier  
- Carrier Code  
- Warehouse  

**dimClients**
- ClientCode  
- ClientName  
- City  
- Country  

### Relationships
- dimCarriers[Carrier Code] 1 → * factInvoices[Carrier Code]  
- dimClients[ClientCode] 1 → * factInvoices[ClientCode]  

![Model View](images/model_view.png)

---

## 📊 Dashboard Preview

![Dashboard Overview](images/dashboard_overview.png)

---

## 📂 Supporting Documentation
- Data Cleaning Steps → `docs/Data_Cleaning_Notes.md`
- Visualisations Logic → `docs/Visualisations.md`
```

---

# 📄 docs/Data_Cleaning_Notes.md

```md
# 🧹 Data Cleaning Notes

## Carriers Details (PDF)
- Filter null rows from Column 4 and Column 1  
- Delete Column 2 and Column 3  
- Promote first row as headers  
- Split carrier field using delimiter: space - space  
- Rename columns to Carrier Code and Carrier  

## ClientsBase (CSV)
- Delete all empty columns  
- Load dataset  

## Invoice Records (Excel)
- Remove promotional headers  
- Change data types via Applied Steps  
- Filter null Invoice Numbers  
- Promote first row to headers  
```

---

# 📄 docs/Visualisations.md

```md
# 📈 Dashboard Visualisations

## Orders by Status
- Visual: Donut Chart  
- Fields: Status, Invoice Number (Count)

## Top 5 Clients Performance
- Visual: Stacked Bar Chart  
- Measure: Count of Orders = COUNTROWS(factInvoices)  
- Fields: Client Name, Count of Orders, Status (Legend)  
- Filter: Top 5 Clients by Count of Orders

## Origin of Late Orders
- Visual: Map  
- Fields: Origin City, Count of Orders (Bubble size)  
- Filter: Status = Late

## Orders Across the Year
- Visual: Stacked Column Chart  
- Fields: Invoice Date (X-axis), Count of Orders (Y-axis)
```

---

Your logistics dashboard project is now **fully portfolio-ready** and properly structured for GitHub submission.

