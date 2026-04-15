# 5. Executive KPI and Target Tracking

<details>
<summary>Click here to see the static Screenshot</summary>

![Screenshot](../../assets/screeenshots/KPI-and-Target-Tracking.png)
</details>

<details>
<summary>Click here to see the interactive GIF</summary>

![GIF](../../assets/screen-recordings/KPI-and-Target-Tracking-GIF.gif)
</details>

---

## What is on this page?
Here is a quick list of what we used:
* **7 Text Cards** (5 top KPIs, 2 bottom right KPIs)
* **2 Slicers** (Region, Date)
* **1 Map Visual** (Total Sales displayed across a global map)
* **1 Goal Gauge/Target Visual** (Total Sales acting against a Target line)
* **1 Treemap** (Profit split inside colored blocks)
* **2 Round Donut Charts** (Total Sales by Region, Total Quantity by Product)
* **1 Line Chart** (Sales moving up and down across the months)

---

## Detailed Explanation

**1. The 7 KPI Number Cards**
* **What they mean:** We put the most important company numbers right at the top flat out: Sales, Quantity, Margin, Average Sales, and Total Profit. The bottom two show Transactions and Customer Count.
* **What they help measure:** This gives completely untrained viewers a 5-second summary of our business health without having to read a chart. 
* **Measures & Fields Used:** Various DAX measures like `Margin`, `Average Sales`, and simple sums like `TotalSales`, `Quantity` from Fact_Sales.

**2. Sales Map & Goal Visual (The Centerpiece)**
* **What they mean:** The Map draws literal bubbles on geographic landmasses to show where money comes from. The big green `41.99K` with a checkmark shows we beat our goal of `40,000`.
* **What they help measure:** The Map helps answer "Where do we sell?" visually. The Target visual acts like a thermometer, telling us strictly if we succeeded or failed our set goal line for that month.
* **Measures & Fields Used:** Map uses `Region` and `TotalSales`. The target visual uses `TotalSales` against a hardcoded DAX measure of `40,000` Target Goal. 

**3. Treemap (Profit by Product)**
* **What it means:** A solid rectangular box chopped into smaller colored rectangles. A huge blue square is "Mouse", and a smaller red box is "Tablet".
* **What it helps measure:** It visually weights which products create the most solid profit block. The bigger the rectangle, the bigger the profit you keep.
* **Measures & Fields Used:** The size of the box is the `Profit` DAX measure, colored using `ProductName` (Products table).

**4. Line Chart & Donut Charts**
* **What they mean:** The line shows the mountains and valleys of our sales journey across January to December. The round donuts cut the pie up by Region percentages and Product percentages.
* **What they help measure:** The line tracks long-term stability or drops. The donuts help you instantly understand market share. (Example: The donut shows a huge dark blue slice proving one product dominates 56% of our quantity!)
* **Measures & Fields Used:** 
  * `TotalSales` against `MonthName` (Date table).
  * `TotalSales` against `Region` (Customers table).
  * `Total Quantity` against `Category` (Products table).
