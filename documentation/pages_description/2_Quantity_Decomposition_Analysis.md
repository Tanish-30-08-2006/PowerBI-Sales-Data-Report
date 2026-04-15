# 2. Quantity Decomposition Analysis

<details>
<summary>Click here to see the static Screenshot</summary>

![Screenshot](../../assets/screeenshots/Quantity-Decomposition-Analysis.png)
</details>

<details>
<summary>Click here to see the interactive GIF</summary>

![GIF](../../assets/screen_recordings/Quantity_Decomposition_Analysis_GIF.gif)
</details>

---

## What is on this page?
Here is a quick list of what we used:
* **2 Slicers** (Date/Time Hierarchy, Region)
* **1 Decomposition Tree** (Breaking down Total Quantity)

---

## Detailed Explanation

**1. Slicers (Filters)**
* **What they mean:** Checkboxes on the right side of the screen let you filter the data by Year/Quarter/Month or by Geographic Region.
* **What they help measure:** You can shrink the focus of the tree structure. For example, you can choose "North" region and "2023" to see exactly what items made up the quantity for only that area and time.
* **Measures & Fields Used:** Date Hierarchy (Year, Quarter, Month, Day) from the Date table, and `Region` from the Customers table.

**2. The Decomposition Tree**
* **What it means:** This is the massive branching structure taking up the whole screen. It starts broad with a big root total of `75` quantity sold (when filtered) and splits into branches showing Categories (`Electronics`, `Accessories`), then Products (`Smartphone`, `Laptop`), and ends with their `Unit Price`.
* **What it helps measure:** It acts like a root-cause analyzer. It helps you visually "drill into" a big number like Total Quantity, so you can discover exactly which hidden category or specific product contributed the most to that big number.
* **Measures & Fields Used:** 
  * The main value analyzed is `Quantity` (from Fact_Sales).
  * It splits by fields: `Category` and `ProductName` (from Products table).
  * It ends with `UnitPrice` (from Fact_Sales or Products table) as the final drill-down step to see the ticket price.
