# 1. Running Sales Trend

<details>
<summary>Click here to see the static Screenshot</summary>

![Screenshot](../../assets/screeenshots/Running-Sales-Trend.png)
</details>

<details>
<summary>Click here to see the interactive GIF</summary>

![GIF](../../assets/screen-recordings/Running-Sales-Trend-GIF.gif)
</details>

---

## What is on this page?
Here is a quick list of what we used:
* **3 Display Cards** (Total Sales, Distinct Customers, Total Quantity)
* **6 Slicers** (Product Name, Category, Region, Year, Quarter, Month Name)
* **1 Matrix Table** (Sales and Running Sum organized by Year and Month)
* **1 Area Chart** (Running Sum Sales by Month)

---

## Detailed Explanation

**1. Slicers (Filters)**
* **What they mean:** We have checklists for Product, Category, Region, Year, Quarter, and Month.
* **What they help measure:** They help you filter the whole page to see data for just one specific time or item (like looking *only* at Laptops in 2023).
* **Measures & Fields Used:** `ProductName`, `Category` from the Products table. `Region` from Customers table. `Year`, `Quarter`, `MonthName` from the Date table.

**2. KPI Display Cards**
* **What they mean:** Three big numbers at the top showing our most important overall totals: `545.23K` sales, `20` unique customers, and `592` items sold.
* **What they help measure:** Quick, clear health check on our big numbers.
* **Measures & Fields Used:** 
  * `TotalSales` (Sum of money from Fact_Sales)
  * `CustomerID` (Count of unique buyers from Fact_Sales) 
  * `Quantity` (Sum of items from Fact_Sales)

**3. The Matrix Table**
* **What it means:** A big grid that shows sales money and a running total side-by-side. It splits the numbers across Years (2023 and 2024) and goes down month by month.
* **What it helps measure:** It lets you see exactly how much money we made in a specific month, and how that money piles up over the year.
* **Measures & Fields Used:** `MonthName` and `Year` (from Date table) on the sides and top. `Sum of TotalSales` and a DAX measure for `Running Sum` inside the grid.

**4. The Bottom Area Chart**
* **What it means:** A simple blue mountain holding up the running total across the months.
* **What it helps measure:** It visually proves that our sales continue to pile up steadily month over month to the end of the year. It makes the running total easy to read without looking at hard numbers.
* **Measures & Fields Used:** X-axis uses `MonthName` (Date table), Y-axis uses the `Running Sum` measure.
