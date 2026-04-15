# 3. Product Performance and Transactions

<details>
<summary>Click here to see the static Screenshot</summary>

![Screenshot](../../assets/screeenshots/Product-Performance-and-Transcations.png)
</details>

<details>
<summary>Click here to see the interactive GIF</summary>

![GIF](../../assets/screen-recordings/Product-Performance-and-Transactions-GIF.gif)
</details>

---

## What is on this page?
Here is a quick list of what we used:
* **2 Slicers** (Region, Date Hierarchy)
* **4 Text Cards** (Showing sales grouped by East, South, North, West regions)
* **1 Bar Chart** (Count of Category by Product)
* **1 Pie Chart** (Last Month Sale by Product)
* **1 Simple Table** (Total Transactions per Product)
* **1 Matrix Table** (Sales compared to Last Month Sales across Dates)

---

## Detailed Explanation

**1. Slicers (Filters)**
* **What they mean:** We have drop-down boxes in the middle and right side to pick Regions or specific Years/Months.
* **What they help measure:** They let you look at the product performance through specific lenses, like focusing heavily on just Q2 of 2024.
* **Measures & Fields Used:** `Region` from Customers table, Date hierarchy from Date table.

**2. Bar Chart**
* **What it means:** A flat green chart showing the count of categories for every single product (like Laptop, Mouse, Monitor).
* **What it helps measure:** It shows us exactly how many items belong to each specific product bucket. 
* **Measures & Fields Used:** X-axis uses `Count of Category` (from Products), Y-axis uses `ProductName` (from Products).

**3. Pie Chart**
* **What it means:** A round chart sliced into colors showing the sales makeup by product name specifically for the *previous* month.
* **What it helps measure:** Instead of looking at all-time sales, this instantly answers "What product made us the most money just recently?".
* **Measures & Fields Used:** A DAX measure calculating `Last Month Sale`, split into colors by `ProductName`.

**4. Tables and Matrix**
* **What they mean:** The main table lines up what product had what total amount of transactions. The matrix on the right shows detailed sales numbers per month, stacked directly against the sales from the prior month.
* **What they help measure:** The first table shows physical order volume (how often the product is bought). The matrix helps measure momentum—did we grow sales this month compared to one month ago.
* **Measures & Fields Used:** 
  * `Total Transactions` (Count of SaleID from Fact_Sales) next to `ProductName`.
  * Date fields next to `Sum of TotalSales` and the `Last Month Sale` DAX measure.

**5. Regional Sales Cards**
* **What they mean:** Four big bold numbers at the bottom representing Total Sales in the East, South, North, and West regions.
* **What they help measure:** This gives an instant read on which geographic location is our strongest block of business.
* **Measures & Fields Used:** Sum of `TotalSales` strictly filtered for each specific `Region` from the Customers table.
