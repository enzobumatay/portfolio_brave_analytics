# Frozen Capital Inventory Analytics
### Problem Statement
The company held approximately $21.0M in inventory, with nearly 75% ($15.7M) tied up as frozen capital due to excess stock beyond target inventory levels. The objective was to identify the highest-impact inventory optimization opportunities and evaluate reduction scenarios that could unlock working capital while maintaining adequate stock coverage.

### Dataset Description
The analysis was built on a relational inventory dataset consisting of transactional inventory records and dimensional reference tables, covering 300+ active SKUs, 50 suppliers, 4 regional distribution centers, and historical demand, purchasing, and stock movement data. The model integrates product, supplier, warehouse, and inventory transactions to evaluate excess inventory against target stock levels and quantify frozen capital across the supply chain.

### Analytical Approach & Methodologies
**Dataset Familiarization:**
Explored the relational inventory dataset to understand the business process, data structure, key entities, and relationships between inventory transactions and reference tables.

<div align="center">
  <img width="326" height="409" alt="image" src="https://github.com/user-attachments/assets/ef4e7d1b-d2f5-4e70-8cbd-da7ea8afcb5f" />
</div>

**Data Cleaning & Preparation:**
Used Python (Pandas) to clean, validate, and transform the raw data by handling missing values, correcting inconsistencies, standardizing formats, and preparing analysis-ready datasets.

<div align="center">
<img width="711" height="402" alt="image" src="https://github.com/user-attachments/assets/9c4b13cf-8fbd-46ee-8e2a-f31623f12fac" />
  
<img width="711" height="352" alt="image" src="https://github.com/user-attachments/assets/040b5556-cc8d-4878-b37c-aef442c216db" />
</div>

**Data Modeling & Dashboard Development:**
Built a dimensional data model in Power BI, created DAX measures and KPIs to quantify frozen capital, inventory performance, and working capital release scenarios, and designed an interactive dashboard for executive reporting.

<div align="center">
  <img width="656" height="380" alt="image" src="https://github.com/user-attachments/assets/26547ae0-cf35-4938-bdf9-d008f119f337" />
</div>

<div align="center">
<img width="656" height="380" alt="image" src="https://github.com/user-attachments/assets/57e2b4ce-c3f5-4409-a0ed-4599b84d505a" />
</div>

**Business Insights & Recommendations:**
Analyzed inventory trends to identify excess stock, prioritize high-impact SKUs, evaluate inventory reduction scenarios, and develop actionable recommendations for optimizing working capital.

### Insights and Recommendations
Results showed approximately $21.0M in frozen capital, representing 75% of total inventory value. Scenario analysis demonstrated that reducing frozen inventory by 40% could potentially release approximately $8.4M in working capital. The solution also highlighted the highest-impact SKUs and inventory reduction opportunities to support data-driven inventory optimization decisions.<br>

Based on these findings, the following recommendations are proposed:<br>
1. Prioritize inventory reduction for the highest frozen-capital SKUs while maintaining target stock levels to minimize excess inventory without impacting product availability.
2. Review replenishment and purchasing policies for overstocked products to prevent recurring inventory buildup and improve inventory turnover.
3. Continuously monitor inventory performance, evaluate inventory reduction opportunities, and support data-driven inventory decisions.

### Technology
Python, Power BI, Excel

### Skills
Data Cleaning & Modeling, KPI Development, Business Analysis, Executive Reporting

### Code: 
Access the full code: [Data Cleanup](Frozen_Capital_Proj_Data_Cleanup.ipynb)

### Dashboard: 
Access the dashboard in PDF: [Frozen Capital Dashboard PDF](Frozen%20Capital_dashboard.pdf) <br>
Access the dashboard in pbix: [Frozen Capital Dashboard PBIX](Frozen%20Capital.pbix)

### Dataset:
[Sample Dataset](Project_Frozen_Capital_sample%20dataset.xlsx)
