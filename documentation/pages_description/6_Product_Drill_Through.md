# 6. Product Drill-Through

<details>
<summary>Click here to see the static Screenshot</summary>

![Screenshot](../../assets/screeenshots/Product-Drill-Through.png)
</details>

<details>
<summary>Click here to see the interactive GIF</summary>

![GIF](../../assets/screen_recordings/Product-Drill-Through-GIF.gif)
</details>

---

## What is on this page?
Here is a quick list of what we used:
* **4 Slicers** (Region, Category, Quarter, Date/Month)
* **5 Highlight Cards** (Stating the exact Product drilled into, plus 4 numbers: Sales, Transactions, Quantity, Profit)
* **1 Tracking Line Chart** (Specific Sales Trend by Month)
* **1 Decomposition Breakdown Tree** (Mapping out exactly how this one product makes its money)

---

## Detailed Explanation

**1. Slicers (Filters)**
* **What they mean:** Side panels that let us restrict our search to only specific times like Year 2023, or specific areas like the South.
* **What they help measure:** If a product is failing, these filters let us zero in to see if it failed specifically in one location or during one strict month.
* **Measures & Fields Used:** `Region` (Customers table), `Category` (Products table), Date fields (Date table).

**2. Focus Highlight Cards**
* **What they mean:** Big clear text at the top that isolates a single item. In our screenshot, the top text confirms we are isolating the `Mouse`. It then shows the exact custom numbers for just the Mouse. 
* **What they help measure:** Whenever you click "Drill Through" from another page, this confirms to the user exactly what item they are investigating. 
* **Measures & Fields Used:** `ProductName` is isolated in the first slot. `TotalSales`, `Transactions`, `Quantity`, and `Profit` adjust their totals based purely on that item.

**3. Product-Specific Line Chart**
* **What it means:** A brown mountain chart focusing ONLY on how this isolated product sold over the months.
* **What it helps measure:** It shows the heartbeat of the single product. While our whole company sales might be doing great, this single chart tells us if "Mice" are selling well or dropping off terribly over the year.
* **Measures & Fields Used:** `Sum of TotalSales` mapped against `MonthName` (Date table).

**4. Decomposition Tracking Tree**
* **What it means:** A flowchart branching out. It takes the main `185.87K` Mouse sales and forces it through funnels: Mouse -> Accessories -> South -> Unit Price.
* **What it helps measure:** When you drill down into a specific product, it lets you ask rapid questions. "Why did this sell so much?" "Oh, because the South region bought the vast majority of it at this strong unit price."
* **Measures & Fields Used:** Starts with `TotalSales`, splits by `Category`, splits by `Region`, and terminates at `UnitPrice`.
