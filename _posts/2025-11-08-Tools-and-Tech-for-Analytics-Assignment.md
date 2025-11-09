# CSUSM Tools and Tech for Analytics Assignment
While completing my Masters in Supply Chain Analytics I took a class called 'Tools and Tech for Analytics' taught by Dr Majid Karimi. This post is an overview for the assignments for the class.

The Github repo for the assignment can be found here:
[GitHub](https://github.com/CBJohnson30/CSUSM-OM620-Assignment)

## Business Problem
For this assignment the business problem was to calculate safety stock for a number of SKU's based on a transactional data set.  I was asked to calculate safety stock two different ways. One that assumed a normal distribution and one with empirical quantiles. 

## Data
The data set was a transactional based data set with the following columns:
`sku_number, inventory_type, stocking_type, lead_time, unit_price, manufacturing_site, division_code, transaction_date, order_quantity`
This data set held 400901 transactions over 495 unique SKU numbers. Like any good data set there was some data cleaning that needed to be done. The data cleaning included:
- Data frame formatting
- Handling oddities and anomalies
- Dealing with null values. 

## Data Investigation
To correctly calculate safety stock I needed to filter down to transactions that were going to be stocked. I filtered the dataset to include only transactions that were labeled 'make to stock' and 'finished goods'. Now that my data set was ready to solve the business problem I decided to do some data investigation to learn more about my data set. 
- How many unique SKUs are we working with?
	- 283 unique SKU numbers.
- How many unique Manufacturing Sites are we working with?
	- 15 unique manufacturing sites.
- How many Divisions are we working with?
	- 66 unique divisions.

## Calculating Safety Stock
Part of the project was calculating safety stock two different ways. The first way was assuming a normal distribution and the second was using empirical quantiles. I used service level coefficients of 75%, 90%, and 95% for both calculations. The normal distribution safety stock calculation I used is:

`Service Level Ceofficient * Order Quanity Standard Deviation * Square Roof of Mean Lead Time`

The empirical quantile calculation I used is:

`Empirical Quantile at the Service Level Coefficient - Mean Order Quantity`

### Comparing Results
While both approaches produced results, the empirical quantiles approached looks more realistic for a company to follow. This is because that in the real world data rarely follows a normal distribution. We can look at an example below as proof.
For SKU number '02BA6CA5' at a 95% Service Level Coefficient:

- Normal Distribution says we should have a safety stock level of 29 units while only having a max order of 20. 
- Empirical Quantiles says we should have a safety stock level of 11 units. 

While there are other factors that would be considered selecting a safety stock level for a SKU. With the information that was provided for this assignment I would recommend using the safety stock values provided by the empirical quantiles approach.