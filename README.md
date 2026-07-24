# Inventory Optimization
## ❔Problem Statement
The company held approximately $21.0M in inventory, with nearly 75% ($15.7M) tied up as frozen capital due to excess stock beyond target inventory levels. The objective was to identify the highest-impact inventory optimization opportunities and evaluate reduction scenarios that could unlock working capital while maintaining adequate stock coverage.

## 📊 Dataset Description

The analysis was built on a relational inventory dataset consisting of transactional inventory records and dimensional reference tables, covering 300+ active SKUs, 50 suppliers, 4 regional distribution centers, and historical demand, purchasing, and stock movement data. The model integrates product, supplier, warehouse, and inventory transactions to evaluate excess inventory against target stock levels and quantify frozen capital across the supply chain.

## 🔍 Analytical Approach & Methodologies

**1. Data Ingestion & Engineering (Python Staging Pipeline)***
Before conducting any analysis, the raw data from our five source tables must be standardized and cleansed to ensure complete data integrity.
* **Systematic Cleaning:** Processing incoming transaction and demand records to eliminate duplicate entries and align date fields to a uniform `MM/DD/YYYY` timeline structure.
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
