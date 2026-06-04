# Inventory Optimization
## ❔Problem Statement
Our company currently has around $344M tied up in excess material inventory exceeding safety stock baselines, which significantly restricts our free cash flow. The goal is to reduce this frozen capital by over $50M, bringing our total category exposure down without risking operational stockouts.

## 📊 Dataset Description

The dataset consists of five tables partitioned into dimensional reference tables and transaction logs, tracking 300 active SKUs, 50 global vendors, and 4 regional hubs. It bridges downstream fulfillment requirements against upstream supply logs to identify excess stock relative to baseline safety margins.

### Table Summaries

* **`Product_Master` (Dimension)** - Contains static item attributes (SKU, Product_Name, Category, Storage_Type), procurement rules (Lead_Time_Days, Min_Order_Qty), and financial baselines (Unit_Cost, Safety_Stock_Level) used to determine the exact threshold for capital overages.
* **`Supplier_Master` (Dimension)** - Captures corporate identities (Supplier_Name), geographic origins (Country), rating tiers (Supplier_Rating), and contract types to audit structural network vulnerabilities.
* **`Warehouse_Master` (Dimension)** - Manages localized distribution properties, identifying explicit facility codes (WH1–WH4) and their volumetric capacities.
* **`Inventory_Transactions` (Fact)** - A dynamic activity log recording individual stock movements (Transaction_Type, Quantity) and post-transaction running stock levels (Current_Stock) to flag systemic deficits.
* **`Daily_Demand` (Fact)** - Tracks historical consumer fulfillment signals (Demand_Qty) and logs systematic metadata markers (Data_Quality_Flag) to isolate structural gaps without losing entry integrity.

## 🔍 Analytical Approach & Methodologies

**1. Data Ingestion & Engineering (Python Staging Pipeline)***
Before conducting any analysis, the raw data from our five source tables must be standardized and cleansed to ensure complete data integrity.
* **Systematic Cleaning:** Processing incoming transaction and demand records to eliminate duplicate entries and align date fields to a uniform `MM/DD/YYYY` timeline structure.
* **Missing Data Imputation:** Rather than dropping incomplete records and losing valuable operational context, rows with missing values (such as the 48 rows in `Daily_Demand`) are systematically flagged as "Missing Data" to isolate the gaps without skewing totals.
* **Anomaly Identification:** Building logical checks within the python data pipeline to automatically isolate and flag systemic operational defects, such as the negative balances observed on `SKU0001` and `SKU0091`.

**2. Relational Data Modeling (Power BI Star Schema)**
To enable fast, intuitive slicing of complex data points across different business angles, the data is structured into an optimized Star Schema model within Power BI.
* **Dimensional Modeling:** Separating static lookup tables (`Product_Master`, `Supplier_Master`, `Warehouse_Master`) from dynamic event logs (`Inventory_Transactions`, `Daily_Demand`).
* **Relationship Optimization:** Establishing strict 1-to-Many (`1:*`) relationships with active filters flowing from the dimension tables down to the fact tables, ensuring that any visual slice by category, supplier, or location immediately updates calculations correctly.

**3. Quantitative Financial Analytics (Overage Isolation)**
The core diagnostic mechanism of this project relies on bridging financial metrics against operational guardrails to expose exact capital blockages.
* **Capital Cost Multipliers:** Utilizing the `Unit_Cost` variable from the product master as a baseline financial weight against physical stock quantities.
* **Safety Stock Baselines:** Comparing actual historical transaction balances against the fixed `Safety_Stock_Level` thresholds. Any volume sitting above this baseline is mathematically isolated as "Frozen Capital," allowing us to pinpoint precisely where the $344M is stuck.

**4. Supply Chain Risk & Bottleneck Diagnosis**
To ensure that cutting $50M of frozen capital does not lead to operational stockouts, the approach blends financial cleanup with supply chain safety metrics.
* **Lead-Time vs. Excess Correlation:** Analyzing the relationship between a supplier's `Lead_Time_Days` and the volume of excess inventory held for their products to determine if over-ordering is a coping mechanism for unreliable vendor nodes.
* **Demand Buffer Testing:** Simulating stock reductions against historical `Demand_Qty` values to confirm that optimized inventory targets can safely absorb peak consumption periods without dropping into a deficit.

**5. Data Visualizations**
* **Donut Chart**
  * *Purpose:* Identifies which product categories hold the highest share of trapped cash.
  * *Metrics:* Frozen Capital % by Category.
* **Horizontal Bar Chart**
  * *Purpose:* Targets immediate cost-cutting by ranking the worst individual products.
  * *Metrics:* Top 10 SKUs by Excess Dollar Value.
* **Map / Bubble Visual**
  * *Purpose:* Spotlights geographic stock imbalances across regional facilities.
  * *Metrics:* Frozen Capital Distribution by Warehouse.
* **Scatter Plot**
  * *Purpose:* Correlates vendor behaviors with over-ordering tendencies.
  * *Metrics:* Lead Time Days vs. Excess Stock Value.
* **Stacked Bar Chart**
  * *Purpose:* Exposes procurement constraints tied to vendor tiers and agreement structures.
  * *Metrics:* Frozen Capital by Contract Type and Supplier Rating.
* **Interactive Matrix Table**
  * *Purpose:* Serves as an operational worksheet for planners to execute SKU-level reductions.
  * *Metrics:* SKU, Current Stock vs. Safety Stock, Over-Target Units, Dollar Savings, and Stockout Risk.

## Insights
