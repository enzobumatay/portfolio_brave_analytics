# Inventory Optimization
## ❔Problem Statement
Our business currently has ~$61.M tied up in excess Packaging and Chemicals inventory, which significantly restricts our free cash flow. The goal is to reduce this frozen capital by over $12M, bringing our total category exposure down to under $50M without risking stockouts.

_Which months show the lowest customer demand for Packaging and Chemicals, allowing us to safely cut back our order sizes and free up that $12M?_  

## 📊 Dataset Description

The dataset contains transactional and master data for our organization's supply chain network. It tracks **500 unique products (SKUs)** across **3 physical warehouses**, monitoring historical customer demand alongside daily warehouse inventory movements.

#### 1. The Core Analytical Sheets (Used for this Project)
These sheets contain the historical timelines and financial figures needed to optimize our inventory and free up frozen capital:
*   **`Daily_Demand` (10,000 Rows):** A comprehensive log tracking exactly how many units of each product customers requested per day. This serves as our source of truth for identifying seasonal customer buying waves and finding the "slow months."
*   **`Product_Master` (500 Rows):** A catalog of every product handled by the company, detailing its broader category (such as *Packaging* and *Chemicals*) and its wholesale unit cost. This allows us to convert physical stock volume into actual corporate dollars to isolate exactly where cash flow is bottlenecked.

#### 2. Supporting Network Sheets
These sheets provide operational context regarding how inventory moves through the supply chain and where it physically sits:
*   **`Inventory_Transactions` (5,000 Rows):** A ledger of warehouse floor activities tracking inventory coming in from suppliers (`IN`) and inventory leaving to fulfill orders (`OUT`), while monitoring the remaining safety stock levels.
*   **`Warehouse_Master` (3 Rows):** A structural table defining the three distribution hubs (`WH1`, `WH2`, `WH3`) and their maximum physical storage capacity thresholds.
*   **`Supplier_Master` (50 Rows):** A vendor profile list tracking the names, geographic locations, contractual agreements, and performance ratings of the company's third-party suppliers.

---

### 🛠️ Sheets & Columns

To answer the core analysis question, data is extracted from the primary sheets and mapped to specific business purposes below:

| Source Sheet | Column Name | Business Description / Purpose |
| :--- | :--- | :--- |
| **Product Master** | `SKU` | The unique product ID used to link our product details to our daily sales records. |
| **Product Master** | `Category` | Used to filter our data down exclusively to **Packaging** and **Chemicals**. |
| **Product Master** | `Unit_Cost` | The dollar price of a single item, used to calculate how much cash is frozen. |
| **Daily Demand** | `Date` | Used to group our sales data by **Month** so we can spot the slow seasons. |
| **Daily Demand** | `Demand_Qty` | The physical number of items customers bought, showing us exactly when demand drops. |

---

## 🚀 Analytical Approach

1.  **Filter:** Isolate the data entries belonging exclusively to the `Packaging` and `Chemicals` product categories.
2.  **Calculate Financial Impact:** Multiply `Demand_Qty` by `Unit_Cost` to translate physical item quantities into total capital value.
3.  **Identify Seasonality:** Aggregate and plot the calculated financial baseline across the `Date` column by month to highlight predictable demand drops (the target "slow seasons").

## Methodologies
### 📈 Key Metrics, Analysis, and Visualizations

To validate the strategy during consultation, the analysis will focus on specific operational indicators, metrics, and visual tools:

#### 1. Key Performance Indicators (KPIs)
*   **Total Trapped Capital ($):** Quantifies the absolute corporate dollar value currently frozen in warehouse inventory.  
    *   *Columns:* `Demand_Qty`, `Unit_Cost`, `Category`
*   **Monthly Demand Volatility (%):** Identifies demand fluctuations, comparing peak consumption months against target slow periods.  
    *   *Columns:* `Date`, `Demand_Qty`
*   **Free Cash Flow Potential ($):** Tracks total projected dollar savings achievable during low-demand months to monitor progress toward the target.  
    *   *Columns:* `Demand_Qty`, `Unit_Cost`

#### 2. Values to Compute
*   **Monthly Financial Demand:** Total capital value demanded by customers per calendar month.  
    *   *Formula:* $\sum (\text{Demand\_Qty} \times \text{Unit\_Cost})$ grouped by Month.
    *   *Columns:* `Date`, `Demand_Qty`, `Unit_Cost`
*   **Average Monthly Baseline:** The typical demand benchmark used to systematically separate "low-demand" months from high-demand months.  
    *   *Formula:* Average (Mean) of the monthly financial demand values.
    *   *Columns:* `Demand_Qty`, `Unit_Cost`
*   **Potential Capital Release:** The direct cash savings retained by reducing purchasing budgets during slower months.  
    *   *Formula:* Current Monthly Spend $-$ Proposed Reduced Spend Target.
    *   *Columns:* `Demand_Qty`, `Unit_Cost`

#### 3. Statistical Analysis Approaches
*   **Time-Series Aggregation:** Summarizing daily granular transaction details into clear, high-level monthly calendar timeframes.  
    *   *Columns:* `Date`, `Demand_Qty`
*   **Descriptive Statistics (Min/Max/Mean):** Pinpointing the historic demand floor (valleys) and demand ceilings (peaks) across the timeline.  
    *   *Columns:* `Demand_Qty`, `Unit_Cost`
*   **Percentage-from-Baseline Analysis:** Calculating how far below the average baseline a slow month drops to justify the exact scale of the procurement cutback safely.  
    *   *Columns:* `Date`, `Demand_Qty`

#### 4. Proposed Stakeholder Visualizations
*   **Seasonal Demand Line Chart:** A monthly timeline visualization highlighting the sharp seasonal valleys where purchasing orders can be safely dialed back.  
    *   *Columns:* `Date` (X-axis), *Calculated Monthly Financial Demand* (Y-axis)
*   **Category Spend Breakdown (Bar Chart):** A side-by-side comparison of total tied-up capital between Packaging vs. Chemicals to reveal which category offers the fastest route to savings.  
    *   *Columns:* `Category` (X-axis), *Total Financial Value* (Y-axis)
*   **Target vs. Actual Bullet Chart:** A straightforward linear tracker showing executive leadership exactly how much of the target **$\$12\text{M}$** capital has been successfully unlocked.  
    *   *Columns:* *Calculated Potential Capital Release*

## Insights
