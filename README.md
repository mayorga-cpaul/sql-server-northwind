
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

![alt text](https://subir-imagen.com/i/m4O0S)

## **The SQL SELECT DISTINCT Statement**

The statement is used to return only different (different) values. SELECT DISTINCT
Within a table, a column often contains many duplicate values; and sometimes you just want to list the different (different) values.
For example: 
```
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
> Below is a selection from the "Customers" table in the Northwind sample database:

![alt text](https://subir-imagen.com/i/DISTINCT)

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

![alt text](https://subir-imagen.com/i/WHERE)

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

