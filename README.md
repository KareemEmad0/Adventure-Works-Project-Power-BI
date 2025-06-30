# Adventure Works Sales Dashboard (Power BI)

This project presents a dynamic Power BI dashboard built from the Adventure Works dataset, focusing on analyzing and visualizing key sales and operational metrics.

## 📊 Dashboard Overview

The dashboard covers:

- 💰 Total Revenue Metrics: SubTotal, Tax, Freight, and Total Due  
- 🚚 Orders by Shipping Method and Online Order Flag  
- 📦 Order Quantity by Product Category  
- 📅 Order Trends over Time: Order Date vs. Ship Date vs. Due Date  
- 👥 Top Customers by Order Count  
- 🌍 Regional Performance: Orders and Revenue by Sales Territory  

## 📷 Screenshots

### Main Dashboard View  
![Dashboard Screenshot](https://github.com/user-attachments/assets/efc18891-b5a7-45ee-9294-3b33d8d498ab)

### Data Model View  
![Data Model Screenshot](https://github.com/user-attachments/assets/bf78b46e-b556-43cc-9230-986e9383b145)

## 🚀 How to Use

1. Clone this repo or download the `.pbix` file.
2. Open it in **Power BI Desktop**.
3. If prompted with a broken data connection:
   - Go to **Home > Transform Data > Data Source Settings**.
   - Click **Change Source** and browse to your local SQL Server database.
   - Replace the server and database names with your own.
   - Example:  
     From:  
     ```
     Server: localhost  
     Database: AdventureWorks2022
     ```  
     To:  
     ```
     Server: YOUR_SERVER_NAME  
     Database: YOUR_DATABASE_NAME
     ```
4. Refresh the data if needed.

> ⚠️ This report was originally built on `AdventureWorks2022` SQL database.  
> If you don't have it, you can download it here:  
> [AdventureWorksDW2019.bak (official Microsoft repo)](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks)

## 🧠 Key DAX Measures

```DAX
# Orders = DISTINCTCOUNT(OrderDetails[OrderID])
# Qty = SUM(OrderDetails[OrderQty])
Total SubTotal (USD) = SUM(OrderDetails[LineTotal])
TotalDue (USD) = [Total SubTotal (USD)] + [TotalTax (USD)] + [TotalFreight (USD)]
TotalFreight (USD) = SUM(OrderDetails[FreightSolve])
TotalTax (USD) = SUM(OrderDetails[TaxAmtSolve])

# Orders by Due Date = 
CALCULATE(
    DISTINCTCOUNT(OrderDetails[OrderID]),
    USERELATIONSHIP(Dates[Date], OrderDetails[DueDate])
)

# Orders by Order Date = 
CALCULATE(
    DISTINCTCOUNT(OrderDetails[OrderID])
)

# Orders by Ship Date = 
CALCULATE(
    DISTINCTCOUNT(OrderDetails[OrderID]),
    USERELATIONSHIP(Dates[Date], OrderDetails[ShipDate])
)
```
## 📩 Contact

Feel free to reach out on [LinkedIn](https://www.linkedin.com/in/kareem-emad0/) or email at kareememad28@gmail.com for collaboration or feedback.
