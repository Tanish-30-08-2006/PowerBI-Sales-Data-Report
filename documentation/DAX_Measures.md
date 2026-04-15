# Power BI DAX Measures Documentation

This document contains all the customized DAX (Data Analysis Expressions) measures created for the Sales Data Report. They are logically categorized below based on their functional purpose within the dashboard.

---

## 1. Base Aggregation Measures
Core calculations used to find total sums, averages, and counts across the dataset.

```dax
SumofSales = SUM(Fact_Sales[TotalSales])

Distinct Customer Count = DISTINCTCOUNT((Fact_Sales[CustomerID]))

Total Quantity = SUM(Fact_Sales[Quantity])

Total Transactions = COUNT(Fact_Sales[SaleID])

Average Sales = AVERAGE(Fact_Sales[TotalSales])

Target = 40000
```

---

## 2. Time Intelligence Measures
Calculations designed specifically to compare sales across different dates, months, and years dynamically.

```dax
Last Month Sale = CALCULATE([SumofSales], DATEADD(Dim_Date[Date], -1, MONTH))

Last Year Sales = CALCULATE([SumofSales] , SAMEPERIODLASTYEAR(Dim_Date[Date]))

Running Sum Sales = 
CALCULATE(
    [SumofSales],
    FILTER(
        ALLSELECTED('Dim_Date'),
        'Dim_Date'[Date] <= MAX('Dim_Date'[Date])
    )
)
```

---

## 3. Profitability Measures
Formulas assessing the bottom line, applying a standard 80% cost reduction to find clear margin numbers.

```dax
Profit = SUM(Fact_Sales[TotalSales]) * (0.8)

Profit Margin % = DIVIDE([Profit], SUM(Fact_Sales[TotalSales]), 0)

Sales Margin = 
VAR Cost = (0.8) * [SumofSales]
VAR Revenue = [SumofSales] 
VAR SalesMargin = Revenue - Cost 
RETURN SalesMargin
```

---

## 4. Regional Filtering Measures
Strictly calculated sums restricted to exact geographical areas (used heavily in the regional breakdown cards).

```dax
Sales East Region = CALCULATE(SUM(Fact_Sales[TotalSales]) , Dim_Customers[Region]="East")

Sales North Region = CALCULATE(SUM(Fact_Sales[TotalSales]), Dim_Customers[Region]="North")

Sales South Region = CALCULATE(SUM(Fact_Sales[TotalSales]), Dim_Customers[Region]="South")

Sales West Region = CALCULATE(SUM(Fact_Sales[TotalSales]) , Dim_Customers[Region]="West")
```

---

## 5. Extremes (Min & Max Variables)
Simple range checks for unit pricing and item quantities.

```dax
Max Quantity = MAX((Fact_Sales[Quantity]))
Max Unit Price = MAX(Fact_Sales[UnitPrice])

Min Quantity = MIN(Fact_Sales[Quantity])
Min Unit Price = MIN(Fact_Sales[UnitPrice])
```

---

## 6. Dynamic Labels & Text Formatting
String concatenation formulas used directly inside visual text cards to provide clean integer formatting and thousands/K suffix labels.

```dax
Status Sale label = IF([SumofSales]>5000 , "High" , "Low")

Total Profit Label = 
VAR total_profit = (0.8)*(SUM(Fact_Sales[TotalSales]))
VAR total_profit_label = "Total Profit : " & FORMAT(total_profit,"#,##0,K")
RETURN total_profit_label

Total Quantity Label = 
VAR total_quantity = SUM(Fact_Sales[Quantity])
VAR total_quant_label = "Total Quantity  : " & FORMAT(total_quantity, "#,##0")
RETURN total_quant_label

Total Sales Label = 
VAR total_sales = SUM(Fact_Sales[TotalSales])
VAR total_sales_label = "Total Sales : " & FORMAT(total_sales, "#,##0,K") 
RETURN total_sales_label
```

---

## 7. Power BI Field Parameters (Dynamic Switchers)
Advanced "What-If" parameter tables generated to dynamically switch the axis of charts without needing multiple visuals.

```dax
Select Parameter = {
    ("SumofSales", NAMEOF('Fact_Sales'[SumofSales]), 0),
    ("Total Quantity", NAMEOF('Fact_Sales'[Total Quantity]), 1),
    ("Profit", NAMEOF('Fact_Sales'[Profit]), 2),
    ("Total Transactions", NAMEOF('Fact_Sales'[Total Transactions]), 3)
}

Metric Picker Category = {
    ("SumofSales", NAMEOF('Fact_Sales'[SumofSales]), 0),
    ("Sales North Region", NAMEOF('Fact_Sales'[Sales North Region]), 1),
    ("Sales South Region", NAMEOF('Fact_Sales'[Sales South Region]), 2),
    ("Sales West Region", NAMEOF('Fact_Sales'[Sales West Region]), 3),
    ("Total Quantity", NAMEOF('Fact_Sales'[Total Quantity]), 4)
}

Metric Picker Product Name = {
    ("SumofSales", NAMEOF('Fact_Sales'[SumofSales]), 0),
    ("Total Quantity", NAMEOF('Fact_Sales'[Total Quantity]), 1)
}
```
