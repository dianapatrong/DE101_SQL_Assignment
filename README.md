# DE101 - SQL Assignment

## About the dataset

We have a Brazilian e-commerce public dataset of orders placed at [Olist Store](https://olist.com/pt-br/), the largest department 
store in Brazilian marketplaces. Olist helps to connect small businesses from all over Brazil, these merchants are able to sell their products 
through the e-commerce site and ship their products directly to the costumers using Olist logistic partners. 

* An order might have multiple items.
* Each item might be fulfilled by a distinct seller.

> Note: This dataset contains real commercial data, all text identifying stores and partners where anonymized by replacing
> the data with the names of Game of Thrones houses.


## The data 
This dataset contains information of 100,000 orders from 2016 to 2018 made at multiple marketplaces in Brazil. With this data 
we can view an order from multiple dimensions: order status, price, payment,  customer location, product attributes and  reviews
written by customers. 

There are 9 flat csv files representing this dataset: 

### 1. Orders dataset
This is the core dataset. From each order you might find all other information.

**File**: [olist_orders_dataset.csv](olist_dataset/olist_orders_dataset.csv)

### 2.  Customers dataset
This dataset has information about the customer and its location. Use it to identify unique customers in the orders 
dataset and to find the orders delivery location. At the olist system each order is assigned to a unique customerid. 
This means that the same customer will get different ids for different orders. The purpose of having a customerunique_id 
on the dataset is to allow you to identify customers that made repurchases at the store. Otherwise you would find that 
each order had a different customer associated with.

**File**: [olist_customers_dataset.csv](olist_dataset/olist_customers_dataset.csv)

### 3. Sellers dataset
This dataset includes data about the sellers that fulfilled orders made at Olist. Use it to find the seller 
location and to identify which seller fulfilled each product.

**File**: [olist_sellers_dataset.csv](olist_dataset/olist_sellers_dataset.csv)

### 4. Reviews dataset
This dataset includes data about the reviews made by the customers.
After a customer purchases the product from Olist Store a seller gets notified to fulfill that order. 
Once the customer receives the product or the estimated delivery date is due, the customer gets a satisfaction survey 
by email where he can give a note for the purchase experience and write down some comments.

**File**: [olist_order_reviews_dataset.csv](olist_dataset/olist_order_reviews_dataset.csv)

### 5. Order items dataset
This dataset includes data about the items purchased within each order.

**Example**
The order_id = `00143d0f86d6fbd9f9b38ab440ac16f5` has 3 items (same product). Each item has the freight calculated 
accordingly to its measures and weight. To get the total freight value for each order you just have to sum.

The total order item value is: `21.33 * 3 = 63.99`

The total freight value is: `15.10 * 3 = 45.30`

The total order value (product + freight) is: `45.30 + 63.99 = 109.29` 

**File**: [olist_order_items_dataset.csv](olist_dataset/olist_order_items_dataset.csv)

### 6. Products dataset
This dataset includes data about the products sold by Olist.

**File**: [olist_products_dataset.csv](olist_dataset/olist_products_dataset.csv)


### 7. Geolocation dataset
This dataset has information Brazilian zip codes and its lat/lng coordinates. You can use it to plot maps and find 
distances between sellers and customers.

**File**: [olist_geolocation_dataset](olist_dataset/olist_geolocation_dataset)


### 8. Payments dataset
This dataset includes data about the orders payment options.

**File**: [olist_order_payments_dataset.csv](olist_dataset/olist_order_payments_dataset.csv)

### 9. Categories
In this data you can find the translated product category name to english.

**File**: [product_category_name_translation.csv](olist_dataset/product_category_name_translation.csv)


## Data Model
The data model for this dataset is described in the picture below: 
![Olist Dataset Model](documentation_images/olist_dataModel.png)


## ✏️  Exercises:
1. [Design the database model](#Exercise1) 
2. Create a normalized data schema 
3. Create the DDL's and load the data
4. Create objects or stored procedures 
5. Answer some questions

## Exercise 1: Design the database model 



Design a DB from hypothetical scenario 

Create DDLs statements  

Create Image and container for the DB 

Queries from their DB schema 

Stored Procedures/User Defined Functions excercises 