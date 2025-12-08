# powerbi-portfolio
A collection of Power BI dashboards with documentation and project details
# Power BI – African Car Sales Dashboard

## 📌 Project Overview

This project is an end-to-end **Power BI sales analytics solution** built on a fictional but realistic **“Top Cars Database – Africa”** dataset.  
It analyses vehicle sales across **dealers in Botswana and South Africa**, answering:

- Which **countries, brands, models, and dealers** drive the most **revenue and profit**?
- How do **quantity sold** and **profit** vary across **brands and segments**?
- Which factors most strongly **influence sales performance**?

The solution is designed to be **portfolio-ready**, with a clean star schema, well-structured DAX, and documented insights.

---

## 🧱 Data Model

The model follows a classic **star schema**:

- **FactSales** – individual sales transactions (revenue, profit, quantity).
- **DimDealer** – dealership locations (country, city, dealer name).
- **DimModel** – vehicle characteristics (brand, model, segment, fuel, engine size).
- **DimDate** – calendar table for time analysis.

Key relationships (1 to many):

- `DimDealer[DealerID]` → `FactSales[DealerID]`
- `DimModel[ModelID]` → `FactSales[ModelID]`
- `DimDate[Date]` → `FactSales[Date]`

---

## 📊 Main KPIs

The following DAX measures power the top-level KPIs:

- **Total Revenue** – `SUM(FactSales[TotalPrice])`
- **Total Profit** – `SUM(FactSales[Total Profit])`
- **Total Quantity Sold** – `SUM(FactSales[Quantity])`
- **Brand Count** – `DISTINCTCOUNT(DimModel[Brand])`
- **Model Count** – `DISTINCTCOUNT(DimModel[Model])`
- **Profit Margin %** – `DIVIDE([Total Profit], [Total Revenue])`

These drive the cards at the top of the dashboard.

---

## 📍 Report Layout

**Sales Dashboard (single page)**

- **KPI Cards:** Total Revenue, Total Profit, Quantity Sold, Count of Brand, Count of Model
- **Donut Chart:** Revenue by Country (Botswana vs South Africa)
- **Bar Chart:** Quantity Sold by Model
- **Combo Chart:** Quantity Sold and Profit by Brand
- **Map:** Revenue & Quantity by Dealer City
- **Key Influencers:** Factors impacting Total Profit / Total Quantity Sold
- **Narrative Text Box:** Explanation of patterns and correlations

Slicers:
- Date range
- Country selection (Botswana, South Africa)

---

## 🧪 Key Influencers

The Key Influencers visual is configured with:

- **Target:** `Total Profit` (or `Total Quantity Sold`)
- **Explain by:** Brand, Model, Segment, Engine Size, Fuel, Country, City, Month

It highlights:
- Premium brands with high profit contribution.
- Volume brands with higher quantities.
- Stronger performance for dealers located in Botswana.
- Higher profit for certain segments and engine sizes.

---

## 📈 Business Insights (Case Study Summary)

- Total revenue in the dataset is **$9.07M**, with **$1.12M** in profit and **347 vehicles** sold.
- **Botswana** generates more revenue than South Africa (about **$6.12M vs $2.96M**), indicating stronger sales or a more premium product mix.
- **BMW, Mercedes-Benz and other premium brands** drive a disproportionate share of **profit**, even when their sales volume is lower than volume brands.
- Models like the **BMW 3 Series, Nissan Qashqai, and VW Polo** appear as top performers in terms of units sold.
- Dealers located in major cities (e.g. Gaborone, Cape Town, Durban) contribute the largest share of revenue and quantity sold.
- Profit and quantity sold are **positively correlated** by brand, but not perfectly – some brands trade off margin vs volume.

These insights support a strategy that:
- Focuses on **premium models and segments** in Botswana and key cities.
- Uses **volume brands** to defend market share while managing margin.

---

## 🛠 How to Use

1. Open the `.pbix` file in **Power BI Desktop**.
2. Review the **Data Model** view to see the star schema.
3. Explore the **Sales Dashboard** page:
   - Filter by country and date.
   - Hover over visuals for detailed tooltips.
   - Use the Key Influencers visual to explore drivers of performance.

---

## 📂 Project Structure

```text
.
├─ data/
│  └─ Top Cars Database - Africa.xlsx
├─ pbix/
│  └─ African Car Sales Dashboard.pbix
├─ docs/
│  ├─ table_dictionary.md
│  ├─ DAX_measures.md
│  └─ transformations.md
└─ README.md
