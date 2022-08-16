## ✏️ Exercise 2: Create the DDL's and load the data
Setup a docker container with a MySQL instance version 8, create all the DDL's and load the data into the tables. 
You will do this according to the **original** schema.

Your file should include: 
* All statements for table creation
* FK definitions
* Indexes whenever they are needed
* Statement to load data into the tables
* **Dockerfile** or **docker-compose.yml** 

⚠️ The teacher should be able to run the file and load the data using your script without problems, so 
remember to include all statements. 


> NOTES: 
> 1. Place all your DDL's in `sol_exercise2.sql` file and place the file in the `Exercise2/Solutions` folder
> 2. Place your `Dockerfile` or `docker-compose.yml` into the `Exercise2/Solutions` folder
> 3. Indexing may be needed in some tables for better performance


### Indexing Performance Example:
This query was executed in two databases, one where the tables had indexes and one without indexes: 
```shell script
SELECT * 
FROM customers 
JOIN orders ON orders.customer_id = customers.customer_id  
JOIN order_items ON order_items.order_id = orders.order_id 
LIMIT 0, 1000
```

| Without indexes | With indexes |
| :---            |    :----:    | 
| 30.126 sec      | 0.230 sec    | 


### Troubleshooting
Here are some issues that you may encounter and how to troubleshoot them. 

---

#### Error Code: 1290. MySQL server is running with the --secure-file-priv option
If you get the error when loading the data from the csv into your table, you need to mount a volume into your container 
pointing to the directory where your files are located to the **--secure-file-prive** path (`/var/lib/mysql-files/`).
```
Error Code: 1290. The MySQL server is running with the --secure-file-priv option so it cannot execute this statement
```

---

#### Error Code: 1292. Incorrect value: '' 
We are going to ignore this kind of error, you can do so in the SQL statements whenever you are loading the data. 

```
Error Code: 1292. Incorrect datatype value: '' for column 'column' at row 1131
```

---

#### Error Code: 1452. Cannot add or update a child row
This error can happen because data is not consistent across files, we most likely have a value in a column on the child table
that does not exist in the column of the parent table. 
```
Error Code: 1452. Cannot add or update a child row: a foreign key constraint fails (`database`.`table`, CONSTRAINT `constraint_ibfk_1` FOREIGN KEY (`column`) REFERENCES `table` (`column`))
```

Since this data is not de-duplicated yet, to solve this error you can set `FOREIGN_KEY_CHECKS=0`, but make sure you set it back 
to 1 after you are done loading the data. 
