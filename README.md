
# **Studying SQL Server** 📝  

> One of the first things they teach us about sql server is the famous (SELECT * FROM Table)
> it is interesting to know that from these notions we can better structure a query.

## **Some of The Most Important SQL Commands**
```
* SELECT - extracts data from a database
* UPDATE - updates data in a database
* DELETE - deletes data from a database
* INSERT INTO - inserts new data into a database
* CREATE DATABASE - creates a new database
* ALTER DATABASE - modifies a database
* CREATE TABLE - creates a new table
* ALTER TABLE - modifies a table
* DROP TABLE - deletes a table
* CREATE INDEX - creates an index (search key)
* DROP INDEX - deletes an index
```
## **We will use norhtwind 🚀**  

* Use [Northwind](https://github.com/DEVLuisEnrique/NorthWind_DB/blob/master/Northwind%20databaseSQL%20SERVER.sql)
* Dowload SQL server [SQL Server](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16) Tutorial [Install](https://www.youtube.com/watch?v=HvNQDkcIKlY)
* Or Postman [Postman](https://www.postman.com/postman/) Tutorial [Install](https://www.youtube.com/watch?v=n5Ec9bMouWQ)

## **Select**

As the word indicates it is occupied to select content of a table is 
composed of:
```
SELECT Column1, Column2... FROM Table_Name; 
SELECT * FROM table_name; --> Select all columns in the table
```
where column1 and column2 are the field names of the table from which you want to select the data

![1](https://user-images.githubusercontent.com/76973247/190881861-eb571e32-3839-4eb1-8d43-be0da8726c97.png)

## **The SQL SELECT DISTINCT Statement**

The statement is used to return only different (different) values. SELECT DISTINCT
Within a table, a column often contains many duplicate values; and sometimes you just want to list the different (different) values.
For example: 
```
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
> Below is a selection from the "Customers" table in the Northwind sample database:

![Distinct](https://user-images.githubusercontent.com/76973247/190881864-a29a8d19-826a-4568-aca3-dca23bb9f1a3.png)

## **The SQL WHERE Clause**

The WHERE clause is used to filter records.
It is used to extract only those records that fulfill a specified condition.

Where Syntax:
```
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```  
**Note:** The WHERE clause is not only used in SELECT statements, it is also used in UPDATE, DELETE, etc.!

![WHERE](https://user-images.githubusercontent.com/76973247/190881866-08787e4e-47e6-44fb-bf82-9972b38b8d69.png)

## **SQL AND OR NOT**

They are conditions that can go within a where and have very important uses 
in the filter of the information so I invite you to practice them.

>* The AND operator displays a record if all the conditions separated by AND are TRUE.
>* The OR operator displays a record if any of the conditions separated by OR is TRUE.
>* The NOT operator displays a record if the condition(s) is NOT TRUE.

```
USE Northwind
Go

SELECT * FROM Customers 
WHERE ContactName = 'Hanna Moos' AND Country = 'Germany'
```

![AND](https://user-images.githubusercontent.com/76973247/190881701-af85f16b-fdc2-4c79-9db3-62f36054bad1.png)

```
USE Northwind
Go

SELECT * FROM Customers 
WHERE ContactName = 'Hanna Moos' OR Country = 'Germany'
```
![OR](https://user-images.githubusercontent.com/76973247/190881725-9b592418-fb54-451a-a4a3-6cc8c1d64f56.png)

```
USE Northwind
GO

SElECT * FROM Customers WHERE NOT City = 'Berlin'
```
![OR](https://user-images.githubusercontent.com/76973247/190881789-d153abaf-16e7-470f-930c-46725cff4ccd.png)

## **SQL ORDER BY Keyword**

Many functions have been implemented in SQL Server, among which ordering stands out 
 `ORDER BY` there are two popular ways to sort ascending `ASC` and descending `DESC`
 these are widely used when you want to take for examplee the highest price of a product then you could order such 
 data in an `ASC` way and take the first
 
 > `Note:` It should be noted that you can order by what suits you best


* Order by value asc
```
USE Northwind
GO

SELECT LastName, FirstName, Address 
FROM Employees 
ORDER BY LastName ASC
```
![ORDER BY](https://user-images.githubusercontent.com/76973247/190886064-4b3647ee-2c5b-4368-a216-0e4fe059e53f.png)

*  Order by value desc

```
USE Northwind
GO

SELECT LastName, FirstName, Address 
FROM Employees 
ORDER BY LastName DESC
```
![DESC](https://user-images.githubusercontent.com/76973247/190886047-72747938-4137-4beb-9828-1577fc7afb7b.png)


## **SQL INSERT INTO Statement**

The SQL INSERT INTO Statement
The INSERT INTO statement is used to insert new records in a table.
INSERT INTO Syntax
It is possible to write the INSERT INTO statement in two ways:
1. Specify both the column names and the values to be inserted:

```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

```
USE Northwind
GO

INSERT INTO Territories (TerritoryID, TerritoryDescription, RegionID)
VALUES (09999, 'Seattle', 2)
```
![INSERT INTO](https://user-images.githubusercontent.com/76973247/190886042-d17057d1-b85b-4a90-b2af-f87566b323be.png)

## **NULL values** 

>What is a NULL Value?
>A field with a NULL value is a field with no value.

>If a field in a table is optional, it is possible to insert a new record or update a record without adding a value to this field. Then, the field will be saved with a NULL value.

>Note: A NULL value is different from a zero value or a field that contains spaces. A field with a NULL value is one that has been left blank during record creation!
>How to Test for NULL Values?
>It is not possible to test for NULL values with comparison operators, such as =, <, or <>.
>We will have to use the IS NULL and IS NOT NULL operators instead.

```
IS NULL Syntax
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
IS NOT NULL Syntax
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```

```
USE Northwind
GO 

SELECT * FROM Employees WHERE Region IS NULL
```
![null](https://user-images.githubusercontent.com/76973247/190886490-66015fa9-7734-4920-8d6e-61ac73bf1fb7.png)




