# Inventory Optimization
## ❔Problem Statement
The company held approximately $21.0M in inventory, with nearly 75% ($15.7M) tied up as frozen capital due to excess stock beyond target inventory levels. The objective was to identify the highest-impact inventory optimization opportunities and evaluate reduction scenarios that could unlock working capital while maintaining adequate stock coverage.

## 📊 Dataset Description
The analysis was built on a relational inventory dataset consisting of transactional inventory records and dimensional reference tables, covering 300+ active SKUs, 50 suppliers, 4 regional distribution centers, and historical demand, purchasing, and stock movement data. The model integrates product, supplier, warehouse, and inventory transactions to evaluate excess inventory against target stock levels and quantify frozen capital across the supply chain.

## 🔍 Analytical Approach & Methodologies
**Dataset Familiarization:**
Explored the relational inventory dataset to understand the business process, data structure, key entities, and relationships between inventory transactions and reference tables.

**Data Cleaning & Preparation:**
Used Python (Pandas) to clean, validate, and transform the raw data by handling missing values, correcting inconsistencies, standardizing formats, and preparing analysis-ready datasets.

**Data Modeling & Dashboard Development:**
Built a dimensional data model in Power BI, created DAX measures and KPIs to quantify frozen capital, inventory performance, and working capital release scenarios, and designed an interactive dashboard for executive reporting.

**Business Insights & Recommendations:**
Analyzed inventory trends to identify excess stock, prioritize high-impact SKUs, evaluate inventory reduction scenarios, and develop actionable recommendations for optimizing working capital.

## Insights
Results showed approximately $21.0M in frozen capital, representing 75% of total inventory value. Scenario analysis demonstrated that reducing frozen inventory by 40% could potentially release approximately $8.4M in working capital. The solution also highlighted the highest-impact SKUs and inventory reduction opportunities to support data-driven inventory optimization decisions.

## Technology
Python, Power BI, Excel

## Skills
Data Cleaning & Modeling, KPI Development, Business Analysis, Executive Reporting

## Code: 
[Data Cleanup](Frozen_Capital_Proj_Data_Cleanup.ipynb)

## Dashboard Sample: 
[Frozen Capital Dashboard](Frozen%20Capital_dashboard.pdf)
