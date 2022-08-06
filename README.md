#DE101 - SQL Assignment

**About the dataset** 

We have a Brazilian e-commerce public dataset of orders placed at [Olist Store](https://olist.com/pt-br/), the largest department 
store in Brazilian marketplaces. Olist helps to connect small businesses from all over Brazil, these merchants are able to sell their products 
through the e-commerce site and ship their products directly to the costumers using Olist logistic partners. 

After a customer purchases the product form Olist Store, a seller gets notified to fulfill that order. Once the customer receives 
the product, or the estimated delivery date is due, the customer gets a satisfaction survey by email where they can rank their satisfaction 
for the purchase experience and write down some comments. 

* An order might have multiple items.
* Each item might be fulfilled by a distinct seller.

> Note: This dataset contains real commercial data, all text identifying stores and partners where anonymized by replacing
> the data with the names of Game of Thrones houses.

This dataset contains information of 100,000 orders from 2016 to 2018 made at multiple marketplaces in Brazil. With this data 
we can view an order from multiple dimensions: order status, price, payment,  customer location, product attributes and  reviews
written by customers. 

There are 9 flat csv files representing this dataset: 
* Customers: olist_customers_dataset.csv has data related to the customer
* Sellers: olist_sellers_dataset.csv contains data related to the registered sellers in Olist
* Reviews: olist_order_reviews_dataset.csv has data related to a review posted by the customer regarding a particular purchased product
* Order items: olist_order_items_dataset.csv contains details of an item purchased 
* Products: olist_products_dataset.csv
* Geolocation: olist_geolocation_dataset.csv
* Categories: product_category_name_translation.csv
* Orders: olist_orders_dataset.csv, it holds the details of an order 
* Payments: olist_order_payments_dataset.csv, contains data associated to the payment details of a particular order

**Data Model**
The data model for this dataset is described in the picture below: 
![Olist Dataset Model](documentation_images/olist_dataModel.png)


### ✏️  Exercises:
1. Create a normalized data schema 
2. Create the DDL's and load the data
3. Create objects or stored procedures 
3. Answer some questions

### ✏️  Exercise 1: Create the DDL's 
