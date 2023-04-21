## Authors 

- Manmohan Dogra (mdogra3@uic.edu)
- Neel Mehta (nmehta32@uic.edu)

## Project Overview

The goal of this project is to develop a tool that predicts which customers are likely to leave a company based on their behavior, such as purchase history, customer service interactions, and demographic data. This information could be used to proactively address customer concerns and reduce churn. Optimizing the supply chain can significantly impact a company's bottom line, reducing costs and improving overall performance. By using data to make informed decisions about supply chain management, companies can improve customer satisfaction, reduce waste and improve their environmental sustainability. 

### Why this problem? 
- Relevance to many industries
- Develop recommendations to make better decisions and improve their operations.

## Data used

For our project, we plan to use the "Mining Company's Global Supply Chain Logistics Data for a Medium-Size Excavator - Extended Dataset" which is available at Table 1: https://data.mendeley.com/datasets/8gx2fvg2k6/1. The table 1 dataset contains 1.8M rows and 53 columns. The data is in tabular form and includes both numerical and categorical variables. The features include order date, lead time, transportation cost, inventory level, supplier information, and order quantity. 
We’re considering to include a Table 2, that associates the weather information related to the location of order origin and destination. We plan to combine both the datasets to see if weather plays a major role in the delivery.  https://www.ncdc.noaa.gov/cdo-web/webservices/v2. 
We will need to preprocess the data, including dealing with missing values and encoding categorical variables, before using it for our analysis.

Here are the columns for the data used: 
```
FIELDS	DESCRIPTION
Type	:  Type of transaction made
Days for shipping (real)     	:  Actual shipping days of the purchased product
Days for shipment (scheduled)	:  Days of scheduled delivery of the purchased product
Benefit per order	:  Earnings per order placed
Sales per customer	:  Total sales per customer made per customer
Delivery Status	:  Delivery status of orders: Advance shipping , Late delivery , Shipping canceled , Shipping on time
Late_delivery_risk           	:  Categorical variable that indicates if sending is late (1), it is not late (0).
Category Id	:  Product category code
Category Name	:  Description of the product category
Customer City	:  City where the customer made the purchase
Customer Country	:  Country where the customer made the purchase
Customer Email	:  Customer's email
Customer Fname	:  Customer name
Customer Id	:  Customer ID
Customer Lname	:  Customer lastname
Customer Password	:  Masked customer key
Customer Segment	:  Types of Customers: Consumer , Corporate , Home Office
Customer State	:  State to which the store where the purchase is registered belongs
Customer Street	:  Street to which the store where the purchase is registered belongs
Customer Zipcode	:  Customer Zipcode
Department Id	:  Department code of store
Department Name	:  Department name of store
Latitude	:  Latitude corresponding to location of store
Longitude	:  Longitude corresponding to location of store
Market	:  Market to where the order is delivered : Africa , Europe , LATAM , Pacific Asia , USCA
Order City	:  Destination city of the order
Order Country	:  Destination country of the order
Order Customer Id	:  Customer order code
order date (DateOrders)	:  Date on which the order is made
Order Id	:  Order code
Order Item Cardprod Id	:  Product code generated through the RFID reader
Order Item Discount	:  Order item discount value
Order Item Discount Rate     	:  Order item discount percentage
Order Item Id	:  Order item code
Order Item Product Price     	:  Price of products without discount
Order Item Profit Ratio	:  Order Item Profit Ratio
Order Item Quantity	:  Number of products per order
Sales	:  Value in sales
Order Item Total  	:  Total amount per order
Order Profit Per Order	:  Order Profit Per Order
Order Region	:  Region of the world where the order is delivered :  Southeast Asia ,South Asia ,Oceania ,Eastern Asia, West Asia , West of USA , US Center , West Africa, Central Africa ,North Africa ,Western Europe ,Northern , Caribbean , South America ,East Africa ,Southern Europe , East of USA ,Canada ,Southern Africa , Central Asia ,  Europe , Central America, Eastern Europe , South of  USA 
Order State	:  State of the region where the order is delivered
Order Status	:  Order Status : COMPLETE , PENDING , CLOSED , PENDING_PAYMENT ,CANCELED , PROCESSING ,SUSPECTED_FRAUD ,ON_HOLD ,PAYMENT_REVIEW
Product Card Id	:  Product code
Product Category Id	:  Product category code
Product Description	:  Product Description
Product Image	:  Link of visit and purchase of the product
Product Name	:  Product Name
Product Price	:  Product Price
Product Status	:  Status of the product stock :If it is 1 not available , 0 the product is available 
Shipping date (DateOrders)   	:  Exact date and time of shipment
Shipping Mode	:  The following shipping modes are presented : Standard Class , First Class , Second Class , Same Day![image](https://user-images.githubusercontent.com/48442342/229414428-e0db0e2f-e22f-4e6e-ad66-c215cce00226.png)

```


## EDA x Feature Engineering

We clea the data, and perform EDA to find corr between the columns, here are the conclusions made from the resulst. 

![Screen Shot 2023-04-02 at 11 42 43 PM](https://user-images.githubusercontent.com/48442342/229413772-32c9b6a3-6789-4203-9eac-0e4316e89fd9.png)

![Screen Shot 2023-04-02 at 11 43 07 PM](https://user-images.githubusercontent.com/48442342/229413711-b51de05c-de26-4084-98c2-8e456cccce5b.png)


Columns that are similar with same values but with different metadata (duplicate columns)
- [Benefit per order], Order Profit per order
- [Sales per customer], Sales, Order Item Total
- [Category ID], Product Category ID, Order Customer ID, Order Item Category ID, Product card ID,
- [Order Item Product Price],Product Price

Unwanted features(null or less correlated values)
- Product Description
- Product Status

## Machine Learning Models 

We use DecisionTreeRegressor to predict the delivery delay: 
- Target features : Days for shipping (real), Days for shipment (scheduled)
- Problem type : Multi-output Regression


## First Evaluation
![image](https://user-images.githubusercontent.com/48442342/229415268-c52a89d5-24b9-44b6-a998-c38264b1d79a.png)









## Model Building 

