
## ✏️ Exercise 4: Create the normalized data model from the existing tables
In this exercise you are going to use the tables that you loaded in Exercise 1 to create the normalized model 
solution given by the teacher.

1. Create the DDL's for the normalized tables
2. Create a new database called **olist_normalized** 
3. Create the statements to load the data, follow the business logic below for de-duplication

This time the constraint check is going to be performed as we are going to omit records that do not match
from our child table to our parent table, so please make sure you have set  `SET FOREIGN_KEY_CHECKS=0;` 


### Business rules: 

1. If there is more than one record with the same `zip_code`, the process of de-duplication will be to do it by
location city in descending order. 

Example: 
The selected record in red is the one that will have to be inserted. 
![Geolocation de-duplication example](documentation_images/geolocation_deduplication.png)

> HINT: Window functions 

2. If a zip code does not exist in the `customers` or `sellers` table, you should default it to zip code 9999, with `DEFAULT`
as the city and state. 

> HINT: You have to add the default value to the `location` table in the normalized db and the `geolocation` table in the original db 

3. All products must have a `category_name` defined, if the value is missing you should update all records with:
    * `nao_classificado` value for Portuguese   
    * `unclassified` value for English translation

4. All products must be categorized correctly, meaning that there should be an entry with the classification name in Portuguese and their
proper translation into English in the `products_category_name_translation` table, if you find any record that is not categorized correctly, 
you need to update records with the following values: 
    * `classificacao_errada` value for Portuguese
    * `wrong_classification` value for English translation


5. A product may be sold by multiple sellers, but a product shouldn't be listed more than once in that sellers' catalog. If a product
appears to be more than once you should consolidate such records in a single one by taking the averages of price and freight_value respectively, 
each value should be rounded to 2 decimals.

Example: 

![Products dedup example - original](documentation_images/products_duplicates.png)

![Products dedup example - result](documentation_images/products_deduplication.png)

> HINT: Window functions 

6. If there's any invalid dates you can update them to `1970-01-02 00:00:00`


7. An order can have multiple products, either the same product or different ones, for the `order_items` table 
you have to aggregate by product_id the quantity of products on a particular order

![Order items dedup example - original](documentation_images/order_items_duplicates.png)

![Order items dedup example - result](documentation_images/order_items_deduplication.png)


Do not set the following: 
````
SET SQL_SAFE_UPDATES=0;
````


> NOTE: 
> 1. Place all your DDL's in `sol_exercise4.sql` file and place the file in the `Solutions` folder
> 

⚠️ The teacher should be able to run the file and load the data into the normalized model using your script without problems, so 
remember to include all statements. 