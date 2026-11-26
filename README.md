**Retail Sales Performance & Business Intelligence Analysis**

**MiniProject Overview**

This project prepares retail sales data in Microsoft Excel and PowerQuery, then analyses it in Microsoft Power BI through a three-page interactive dashboard.

The dashboard covers: 1. Sales Overview 2. Customer & Product Analysis 3. Order & Delivery Analysis

**Dataset**
- Source recorded in the project status report: Hugging Face ---Gokila-dataanalyst/Retail_sales_Dashboard
- Format used for preparation: CSV
- Fields referenced in the project: transaction/order/customer/product identifiers, customer demographics and location, product and brand details, quantity, unitprice, total amount, discount, payment mode, rating, order status, order date and delivery date.
- The project status report does not record the final row count, date range, currency or a complete data dictionary. Add these details from the final prepared workbook before publishing the project.

**Tools**
- Microsoft Excel
- Power Query
- Microsoft Power BI
  
**Workflow**

**1. Excel --- Data Cleaning and Preparation**

The recorded preparation steps include: 
- Downloaded the CSV and imported it into Excel.
- Replaced applicable missing values with Unknown.
- Removed duplicate records.
- Checked data types and removed data-type errors.
- Imputed missing phone-number values with 0 as a placeholder.
- Used Flash Fill to replace blank transaction IDs with Unknown.
- Retained records with an unknown transaction ID when a valid Customer ID was present.
- Removed rows where both Quantity and Unit Price were missing.
- Calculated Gross Sales as Unit Price × calculated Quantity.
- Calculated missing Discount values using Total Amount and Gross Sales.
- Created a Rating Status mapping: - 0 --- NotRated - 1 --- Very Poor - 2 --- Poor - 3 --- Average - 4 --- Good - 5 ---Excellent
- Imputed missing Age values using the average age and an IF-based approach.
- The working status report records an average age of 43.
- Removed records with missing Order Date or Delivery Date rather than estimating either date.
- Created Customer Details, Product Details, Order Details, Sales Details and Date Dimension tables.
- Standardised text fields in Power Query.
- Sorted records in descending order to inspect recent patterns.
  
**2. Power BI --- Data Model**

The model uses Order Details as the central fact table.
The recorded relationships are:
- Order Details ↔ Sales Details --- Transaction ID
-Order Details ↔ Customer Details --- Customer ID
- Order Details ↔ Product Details --- Product ID
- Order Details ↔ Date Dimension --- Order Date


**3. Power BI --- Dashboard Pages**

**Page 1: Sales Overview**


Cards - Total Orders - Total Sales - Net Revenue - Total Quantity -Average Discount - Average Order Value

Visuals 
- Monthly Sales --- line chart
- Total Sales by State --- funnel chart
- Payment Modes --- donut chart
- Orders by Status --- pie chart
- Top 10 Products --- treemap

Slicers: Month, Year, Category, State

Interactions: Clear Filter button, page navigation, drill-through by Category/Product ID/State.

Bookmarks: Top UPI Sales; Sales of Electronics.

**Page 2: Customer & Product Analysis**

Cards - Average Age - Average Rating - Total Products - TotalBrands - Total Orders

Visuals 
- Total Sales by Category --- treemap
- Orders by Age Group --- donut chart
- Top 10 Products --- stacked bar chart
- Orders by Gender --- stacked column chart
- Location of Sales --- map

Slicers: Month, Year, Category, State, Gender

Interactions: Clear Filter button, page navigation, drill-through by Customer ID/Product ID, Back button.

Bookmark: Female Customer Orders.

**Page 3: Order & Delivery Analysis**

Cards - Delivered Orders - Cancelled Orders - Returned Orders - Pending Orders - Shipped Orders - Total Orders

Visuals 
- Yearly Cancellation --- clustered column chart
- Order Status Distribution --- donut chart
- Customer Ratings --- stacked barchart
- Returns by Product Category --- line and stacked column chart
- Monthly Orders --- line chart
- Customer Location --- clustered barchart

Slicers: Month, Year, Category, State, Order Status

Interactions: Clear Filter button, page navigation, drill-through by Order Status, Back button.

Bookmark: 2025 April Sales.

**Important Interpretation Notes**
- Unknown is a missing-value label, not a real customer, product or transaction identity.
- A phone value of 0 is a placeholder and should not be interpreted as a valid phone number.
- Validate the order grain before using COUNT(Transaction_ID) as Total Orders. If a transaction appears on multiple rows, a
  distinct-count or order-level measure may be needed.
- The recorded Average Order Value calculation uses AVERAGE(total_amount). If there are multiple rows per order, validate whether this represents true order-level AOV; a common order-level definition is total revenue divided by distinct orders.
- Records with missing Order Date or Delivery Date were excluded from the prepared analysis, so date-based and delivery-time findings apply to the retained records only.
- The status report documents dashboard components but does not provide final KPI values or quantified business findings. Add insights only after checking the final PBIX report.

**Conclusion**

This project demonstrates a practical analytics workflow from Excel-based data preparation to Power BI modelling and interactive reporting. It is designed to explore retail sales, customer and product patterns, and order-status performance.

**Dataset Attribution**

Dataset: Gokila-dataanalyst/Retail_sales_Dashboard on Hugging Face, as cited in the project status report. Retain the dataset's originalattribution and licence information when sharing the project.
