# Retail-Sales-Performance-Business-Intelligence-Analysis
Mini  Project
EXCEL PHASE
	1. Downloaded csv file
	2. Uploaded the csv file into excel 
	3. Replaced missing values with" unknown"
	4. Removed Duplicates
	5. Cheched the data type and removed errors
	6. Imputed missing phone number column with 0 
	7. Blank Transaction id is replaced by unknown using flash fill
	8. Kept "Unknown" transaction id because valid Customer ID is there unknown transactions
	9. Dropped rows with both quantity and Unit price missing
	10. Found Gross Sales= unitprice* calculated quantity
	11. Calculated missing Discount column  using total amount,and Gross sales
	12. Created columns Rating Status to handle missing values- 0 is imputed and made-- Not Rated,1-Very poor,2-Poor,3-average,4-Good,5- Excellent
	13. Age is calculated by average and imputed the missing column using IF function
	14. Dropped down missing delivery date and order date because Dropping or guessing anyone  date may cause error in the other, For delivery time calculation in analysis it  is better to be dropped
	15. Normalised the dataset to customer details,product details,order details,sales details,date dimension for future analysis using duplicates of cleaned dataset and choose column icon
	16. Made the text standardisation In powerquery using transform function
	17. Sorted datas to see latest pattern- descending sort
	
POWER BI PHASE
	1. Established connections using star schema keeping order details as fact table
		a. Established cardinality between order Detail and sales Detail table by Transaction Id
		b. Established cardinality between order Detail and Customer detail table by Customer ID
		c. Established cardinality between order Detail and Product Detail table by Product ID
		d. Established cardinality between order Detail and Date Dimemension table by order date
	2. 3 buttons for pages 
	3. Sales overview Page created
		a. Cards applied using explicit measures
			i. Total Orders = COUNT(Order_Details[Transaction_ID])
			ii. Total Sales = SUM(Sales_Details[Gross_Sales])
			iii. Net Revenue = SUM(Sales_Details[total_amount])
			iv. Total quantity = SUM(Sales_Details[quantity])
			v. Average Discount = AVERAGE(Sales_Details[Calculated_Discount%])
			vi. Average Order Value = AVERAGE(Sales_Details[total_amount])
			
		b. Charts applied
			i. Line chart :monthly sales
			ii. Funnel Chart :Total Sales by States
			iii. Donut Chart :Payment Modes
			iv. Pie Chart :Order By Status
			v. TreeMap :Top 10 Products
			
		c. Slicers applied
			Month,Year,Category,State
			
		d. Clear Filter Button applied
		e. Page Navigation Buttons for all 3 Pages applied
		f. Added Drill through Category,Product ID and State
		g. Saved bookmarks :
			i. Top UPI sales
			ii. Sales of Electronics
			
			
	4. Customer And Product Page Created
		a. Cards applied using explicit measures
			i. Average Age = AVERAGE(Customer_Details[age])
			ii. Average Rating = AVERAGE(Order_Details[rating])
			
		b. Cards applied using implicit measures
			i. Total Products= Count of products name
			ii. Total Brand= Count of Brands
			iii. Total Orders= Count of Transaction Id
			
		c. Charts Applied
			i. Tree Map  :Total Sales by Category
			ii. Donut Chart: Order By Age Group
			iii. Stacked bar chart: Top 10 Products
			iv. Stacked column Chart: Orders by Gender
			v. Map: Location of Sales
			
		d. Slicers applied
			Month,Year,Category,State,Gender
		
		e. Clear Filter Button applied
		f. Page Navigation Buttons for all Other 2Pages applied
		g. Added Drill through Customer ID,Product ID and inserted back button
		h. Saved bookmarks :
			i. Female Customer Orders
		
		
	5. Order And Delivery Analysis Page Created
		a. Cards applied using explicit measures
			i. Delivered Orders = CALCULATE(COUNT(Order_Details[Transaction_ID]),Order_Details[order_status]="Delivered")
			ii. Cancelled Orders = CALCULATE(COUNT(Order_Details[Transaction_ID]),Order_Details[order_status]="Cancelled")
			iii. Returned Orders = CALCULATE(COUNT(Order_Details[Transaction_ID]),Order_Details[order_status]="Returned")
			iv. Pending Status = CALCULATE(COUNT(Order_Details[Transaction_ID]),Order_Details[order_status]="Pending")
			v. Shipped Status = CALCULATE(COUNT(Order_Details[Transaction_ID]),Order_Details[order_status]="Shipped")
			
		b. Cards applied using implicit measures
			i. Total Orders= Count of Transaction Id
			
		c. Charts Applied
			i. Clustered Column Chart: Yearly cancellation 	
			ii. Donut Chart: Order status Distribution
			iii. Stacked bar chart:Customer Ratings
			iv. Line & Stacked column Chart: Returns by Product Category
			v. Line Chart : Monthly  Orders
			vi. Clustered bar chart:customer Location
			
		d. Slicers applied
			Month,Year,Category,State,Order Status
		
		e. Clear Filter Button applied
		f. Page Navigation Buttons for all Other 2Pages applied
		g. Added Drill through Order Status and inserted back button
		h. Saved bookmarks :
			i. 2025 april Sales
