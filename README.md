# RFM Modeling
RFM Analysis (Recency, Frequency, and Monetary) is based on customer segmentation, grouping them by the sum of RScore, FScore, and Mscore, and assigning a label to each group. The goal of this project is to enable the stakeholders to understand their customers based on segmentation and use marketing tactics to move them from the lowest tier (segment) to the highest.

### Dataset And Data Dictionary:

This dataset is a UCI retail dataset, containing:

**Columns**

1. InvoiceNo: Invoice number. Nominal, a 6-digit integral number uniquely assigned to each transaction. If this code starts with the letter 'c', it indicates a cancellation. 
2. StockCode: Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each distinct product.
3. Description: Product (item) name. Nominal.
4. Quantity: The quantities of each product (item) per transaction. Numeric.	
5. InvoiceDate: Invoice Date and time. Numeric, the day and time when each transaction was generated.
6. UnitPrice: Unit price. Numeric, Product price per unit in sterling.
7. CustomerID: Customer number. Nominal, a 5-digit integral number uniquely assigned to each customer.
8. Country: Country name. Nominal, the name of the country where each customer resides.

And spans between 01/12/2010 and 09/12/2011 (13 months) for a UK-based, registered non-store online retail.

### Tools And Libraries

- Python
- Jupyter Notebook (VsCode)
- Pandas (Data Analysis Library)
- Matplotlib (Visualization)

### Work Flow
- Importing libraries
- Dropped unnecessary columns (needed Invoice Date and Customer ID)
- Dropped duplicated and Null records
- Created "First purchased" column from InvoiceDate column to filter out new customers (They don't have enough data), created a segment for them as "New" label, and also filtered for "old customer".
- Created "Sale" calculated column from Quantity * Unit Price columns
- Grouped customers based on last transaction date Invoicedate (Recency), unique InvoiceNo (Frequency), and Sale (Monetary)
- Rename Columns From Invoicedate, InvoiceNo, and Sales to Recency, Frequency, and Monetary.
- Created Quantile Q1(25%), Q2(50% or median), and Q3(75%), and assigned a "score" (1-4) based on where each customer metric falls within (Lower Recency is good).
- Created the SumScore Column by aggregating Rscore, Fscore, and Mscore, as well as the RFMCode column(Concatenations of all scores)
- Create a label function to assign labels based on the SumScore with less than 3 (Lost), less than 6 (At risk), less than 8 (Moderate), less than 10 (Loyal), and 12 (champion), and create a "segment" column from the labels
- Extract the segment column and merge (joins) it with the old customer data, and also concatenate old customers and new customers to get the distribution "picture."

### Insight 

- Champion label takes about 60% of the distribution (good), Loyal at 20%, Moderate at 10%, At risk at 7%, New at 2% and 1% at Lost.

![Pie Chart](https://github.com/Harbdulahi/RFM-Analysis--Customer-Segmentation--Python-/blob/main/RFM/outputrfmpie.png?raw=true)


![Bar Chart](https://github.com/Harbdulahi/RFM-Analysis--Customer-Segmentation--Python-/blob/main/RFM/up5.jpg?raw=true)


### Recommendation
Feed the data (result) into a CRM and send Marketing message to each segment. 
- For segment such as Champions and Loyal put them into a loyalty program. offer them early access, exclusivity and discount etc.
- For the Moderate segment offer them discount and promote new product to them by offering them a time bound offers.
- For At Risk offer them coupon they can use that has an expiry time. And send marketing message to them occasionally to promote them to upper tiers.

The overall goal of RFM is to understand customer distribution and promote them from lowest tier to the highest tier


[RFM Video](https://youtu.be/UM9QzzjTGUc?si=-ECNSi5XhbaqiDJs)
