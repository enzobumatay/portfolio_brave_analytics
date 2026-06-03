# Inventory Optimization
## ❔Problem Statement
Our business currently has ~$61.M tied up in excess Packaging and Chemicals inventory, which significantly restricts our free cash flow. The goal is to reduce this frozen capital by over $12M, bringing our total category exposure down to under $50M without risking stockouts.

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
1. Monthly Category Spend ($):
What to compute: The total dollar value of customer demand for each month, specifically filtered for Packaging and Chemicals.
Why: This maps our baseline timeline so we can easily spot the high peaks and low valleys.

2. The Demand Floor (The "Low" Benchmark):

What to compute: The average (mean) monthly demand vs. the lowest-performing month's demand.
Why: This tells us exactly how much customer demand drops during the slow season so we know how deep we can cut our order sizes without causing a stockout.

3. The Purchasing Reduction Target (The "Trim"):
What to compute: The difference between our current normal order size and the new, reduced order size for those slow months.
Why: This tells the procurement team exactly what their new, lower order numbers should be when writing contracts with suppliers.

4. Total Unlocked Cash:
What to compute: The running sum of all the budget saved across those slow months.
Why: This is the final scorecard value that proves to the executives that we successfully freed up the target $12M and brought total inventory exposure under $50.

5. visuals:
Seasonal Demand Line Chart: A monthly timeline plot highlighting the sharp seasonal drops (valleys) where we can safely reduce orders.
Category Spend Breakdown (Bar Chart): Comparing the total tied-up capital between Packaging vs. Chemicals to see which category offers the fastest savings.
Target vs. Actual Gauge/Bullet Chart: A simple visual tracker showing leadership how close the proposed cuts get us to freeing up the $12 goal.

## Insights
