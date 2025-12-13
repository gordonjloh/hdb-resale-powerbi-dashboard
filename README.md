# HDB Resale Market Dashboard (Singapore)

Interactive Power BI report to help **policymakers and housing analysts** monitor resale HDB market trends, affordability and spatial patterns across Singapore.

---

## 1. Problem Statement

Singapore’s HDB resale market is a key pillar of housing affordability, but the data is spread across multiple CSV files and is not easy to interpret quickly.  

Policy and planning teams need a **single, interactive view** that answers questions such as:

- How are **resale prices and transaction volumes** evolving over time?
- Which **towns and regions** are becoming more expensive or more active?
- How do **flat type, size and age/lease** affect prices and $/sqm?
- Where are **affordable resale options** still available, and where are they becoming scarce?

This project consolidates resale transaction data into a **Power BI dashboard** that provides an executive overview plus deeper drill-downs on towns, flat types, flat age and affordability.

---

## 2. Data

**Source**

- Public HDB resale flat transaction data (CSV) from data.gov.sg / HDB open data.
- Data dictionary and documentation provided with the dataset.

**Files used (combined into a single fact table in Power BI)**

- `resale-flat-prices-based-on-approval-date-2000-feb-2012.csv`
- `resale-flat-prices-based-on-registration-date-from-mar-2012-to-dec-2014.csv`
- `resale-flat-prices-based-on-registration-date-from-jan-2015-to-dec-2016.csv`
- `ResaleflatpricesbasedonregistrationdatefromJan2017onwards.csv`
- Data Dictionary (PDF)

**Key fields**

- `month` – transaction month  
- `town` – HDB town  
- `flat_type` – e.g. 3-Room, 4-Room, Executive  
- `flat_model` – flat design/model  
- `floor_area_sqm` – floor area in sqm  
- `storey_range` – floor range (e.g. 10–12)  
- `lease_commence_date`, `remaining_lease` – for approximating flat age  
- `resale_price` – total resale price in SGD  

From these, additional calculated fields are created in Power BI, such as:

- **Price_per_sqm** = `resale_price / floor_area_sqm`  
- **Flat_Age** = (transaction year – lease_commence_year)  
- **Age_Band** and **Price_Band** (e.g. `<10 yrs`, `10–29 yrs`, etc.; `<$400k`, `$400k–$700k`, `>$700k`)

---

## 3. Power BI Report Pages

The report is organised into **5–6 pages**:

### Page 1: Executive Summary

**Purpose:** Quick “health check” of the resale market.

**Key elements:**

- KPI cards:
  - Total Transactions  
  - Total Resale Value (S$)  
  - Average Resale Price  
  - Median Resale Price  
  - Average Price per Sqm  
  - YoY % change in Average Price and Transactions
- Trend sparklines / small charts for prices and volume
- Slicers for:
  - Year / Month
  - Town / Region
  - Flat Type

This page lets policymakers see **high-level movements** in volume and prices at a glance.

---

### Page 2: Market Trends Over Time

**Purpose:** Understand how the market evolves over time.

**Typical visuals:**

- Line chart of **Average Resale Price** over time
- Column/line combo for **Number of Transactions** per month/year
- Optional breakdown by:
  - Flat Type
  - Region (Mature vs Non-Mature or custom grouping)

This page helps identify **cycles, peaks, dips and structural shifts** in the resale market.

---

### Page 3: Town & Region Comparison

**Purpose:** Compare prices and activity across Singapore’s towns.

**Typical visuals:**

- Map (ArcGIS or Shape Map) of **Average Price per Sqm** by town
- Bar charts:
  - Transactions by town
  - Average resale price by town
- Slicers for year, flat type, and price bands

This page supports questions such as:

- Which towns are **most expensive / most affordable**?
- Which towns have **high transaction activity**?
- Are certain regions seeing **stronger price growth** than others?

---

### Page 4: Flat Type & Size Insights

**Purpose:** Analyse how flat type and size influence prices.

**Typical visuals:**

- Bar charts:
  - Average price by **Flat Type**
  - Average **Price per Sqm** by Flat Type
- Scatter or line chart:
  - `floor_area_sqm` vs `Price_per_sqm`
- Supporting summary table (flat type × year, with average price and transactions)

This page answers:

- How do **3-Room vs 4-Room vs 5-Room vs Executive** flats compare?
- Do **larger flats** always cost more per sqm, or are there trade-offs between **space and $/sqm**?

---

### Page 5: Flat Age, Lease & Affordability

**Purpose:** Understand the impact of flat age and remaining lease on prices and affordability.

**Typical visuals:**

- Column chart of **Average Price per Sqm by Age_Band**
- Line or bar showing **Average Price vs Remaining Lease**
- Table/visual segmenting:
  - Older vs newer flats
  - Mature vs Non-Mature towns within each age band

This page helps explore:

- Are **younger flats** commanding significant premiums?
- How does **age/lease interact with location** to affect affordability?
- Where might **older but more affordable stock** still be available?

---

### Page 6: Price Bands & Affordability Segments (Optional)

**Purpose:** Provide a simple **affordability lens**.

**Typical visuals:**

- Stacked column or 100% bar chart of **transactions by Price_Band**:
  - e.g. `<$400k`, `$400k–$700k`, `>$700k`
- Breakdown by:
  - Town
  - Flat Type
  - Year

Helps policymakers see:

- How the **share of “affordable” flats** is changing over time.
- Which towns and flat types still have **meaningful volumes of lower-priced units**.

---

## 4. Key Insights (Examples)

Exact insights will depend on slicers and time periods, but the dashboard is designed to support findings such as:

- **Overall market movement**
  - Long-term **upward trend in resale prices**, with periods of cooling or acceleration.
  - Changes in **transaction volumes** following policy interventions or macro conditions.

- **Spatial patterns**
  - **Mature towns** and centrally located areas generally show **higher average prices and price per sqm**.
  - Some **non-mature or fringe towns** still offer relatively **more affordable options**, especially for smaller flat types.

- **Flat type & size trade-offs**
  - Larger flat types (5-Room, Executive) have higher **absolute prices**, but may not always have the highest **price per sqm**.
  - Smaller flats may appear more “affordable” in total price, but can be **expensive on a per-sqm basis**, especially in central locations.

- **Age & lease effects**
  - Newer flats (shorter time since lease commencement) often command **premium prices**, particularly in desirable towns.
  - Older flats may show **discounts per sqm**, but in certain central towns even older units remain relatively expensive.

- **Affordability segments**
  - Over time, the **proportion of very low-priced transactions** can decrease in some towns, signalling **growing affordability pressure**.
  - The dashboard helps identify **which towns and flat types still have meaningful stock** under certain policy-relevant thresholds (e.g. <$400k).

These insights allow policymakers to **monitor affordability**, identify **pressure points**, and support discussions on **supply, grants and policy interventions** in the HDB resale market.

