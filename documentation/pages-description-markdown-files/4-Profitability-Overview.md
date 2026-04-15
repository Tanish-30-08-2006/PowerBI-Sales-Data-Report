# 4. Profitability Overview

<details>
<summary>Click here to see the static Screenshot</summary>

![Screenshot](../../assets/screeenshots/Profitability-Overview.png)
</details>

<details>
<summary>Click here to see the interactive GIF</summary>

![GIF](../../assets/screen-recordings/Profitability-Overview-GIF.gif)
</details>

---

## What is on this page?
Here is a quick list of what we used:
* **3 Slicers** (Product Name, Region, Date)
* **1 Parameter Button Panel** (To change the charts dynamically)
* **1 Percent Card** (Profit Margin %)
* **1 Scatter Plot Chart** (Total Sales and Total Profit dots)
* **1 Column Chart** (Total Sales by Category)
* **1 Area Chart** (Total Sales by Month trendline)
* **1 Bar Chart** (Total Sales ranked by Product)
* **1 Funnel Chart** (Total Sales filtered by Region)
* **1 Pie Chart** (Sale split by Product Name)

---

## Detailed Explanation

**1. Parameter Panel**
* **What it means:** A simple bulleted checklist where you can select "SumofSales", "Total Quantity", "Profit", or "Total Transactions".
* **What it helps measure:** It acts like a magic switch. Clicking a different bullet point instantly updates the other charts to show those items instead of sales, saving screen space.
* **Measures & Fields Used:** A custom Power BI Field Parameter.

**2. Profit Margin Card & Scatter Plot**
* **What they mean:** The bold `80.0%` means we keep 80 cents of every dollar. The plotted line with dots matches up sales value with profit value for each item.
* **What they help measure:** The scatter plot helps us find our "superstars" (items far up and to the right) that bring in a lot of sales AND a lot of profit. 
* **Measures & Fields Used:** DAX measures for `Total Profit` and `Profit Margin %`. The plot uses `Total Sales` on X, `Profit` on Y, and `ProductName` for the dots.

**3. Sales by Category (Column) & Sales by Month (Area)**
* **What they mean:** Two blue columns show Electronics vs Accessories sales. The brown mountain chart shows sales going up or down over the months.
* **What they help measure:** The columns tell us which top-level type of tech makes more money. The mountain chart helps quickly spot seasonal drop-offs or spikes in our business timeline.
* **Measures & Fields Used:** `SumofSales` mapped against `Category` (Products table) and `MonthName` (Date table).

**4. Ranking Bar Chart & Funnel Chart (Right Side)**
* **What they mean:** The big dark blue horizontal bars rank our single products from biggest to lowest. The purple blocks below it act like a funnel, dropping down from East (the biggest region) down to West (the smallest).
* **What they help measure:** Ranking charts immediately tell you who is in 1st place and who is in last place at a glance, without staring at messy numbers. 
* **Measures & Fields Used:** `SumofSales` sorted by `ProductName`, and `SumofSales` sorted by `Region` (Customers table).
