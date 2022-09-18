
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

## **UPDATE**

The SQL UPDATE Statement
The UPDATE statement is used to modify the existing records in a table.

UPDATE Syntax
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
Note: Be careful when updating records in a table! Notice the WHERE clause in the UPDATE statement. The WHERE clause specifies which record(s) that should be updated. If you omit the WHERE clause, all records in the table will be updated!

```
USE Northwind
GO 
UPDATE Employees
SET LastName = 'Lopez', Title = 'Sales Representative'
WHERE EmployeeID = 5; 
 ```
## DELETE

The SQL DELETE Statement
The DELETE statement is used to delete existing records in a table.

DELETE Syntax
DELETE FROM table_name WHERE condition;
`Note:` Be careful when deleting records in a table! Notice the WHERE clause in the DELETE statement. The WHERE clause specifies which record(s) should be deleted. If you omit the WHERE clause, all records in the table will be deleted!

 ```
 DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';
 ```

 ## TOP

The SQL SELECT TOP Clause
The SELECT TOP clause is used to specify the number of records to return.

The SELECT TOP clause is useful on large tables with thousands of records. Returning a large number of records can impact performance.

Note: Not all database systems support the SELECT TOP clause. MySQL supports the LIMIT clause to select a limited number of records, while Oracle uses FETCH FIRST n ROWS ONLY and ROWNUM.

```
USE Northwind
GO

SELECT TOP 3 CustomerID, CompanyName, ContactName FROM Customers
```

| CustomerId  | CompanyName  | ContactName |
| :------------ |:---------------:| -----:|
| ALFKI      | Alfreds Futterkiste | Maria Anders |
| ANATR      | Ana Trujillo Emparedados y helados        |   Ana Trujillo |
| ANTON | are Antonio Moreno Taquería        |    Antonio Moreno |

## Key references in SQL
 ```
In SQL, keywords are the reserved words that are used to perform various operations on the database. There are many keywords in SQL and since SQL is not case sensitive, it does not matter if we use, for example, SELECT or select. LIST OF SQL keywords
 ```

* [KEY](https://laingenieria.info/questions/2369/que-buenas-razones-existen-para-capitalizar-las-palabras-cla#:~:text=SQL%20es%20un%20lenguaje%20orientado%20a%20las%20cl%C3%A1usulas%2C,le%20ayuda%20a%20separar%20visualmente%20las%20cl%C3%A1usulas%20separadas.)
* [MORE ABOUT KEY](https://support.microsoft.com/es-es/office/palabras-reservadas-de-sql-b899948b-0e1c-4b56-9622-a03f8f07cfc8)
* [IS IMPORTANT?](https://www.bing.com/search?q=Importancia+de+las+palabras+clave+en+SQL+SERVER&qs=n&form=QBRE&sp=-1&pq=importancia+de+las+palabras+cla&sc=1-31&sk=&cvid=A43E854C79174B64BAFC3BD90B5E4D6E&ghsh=0&ghacc=0&ghpl=)

| **Keyword**  | **Description**  | 
| :------------ |:--------------- |
| ADD      | Adds a column in an existing table |
| ADD CONSTRAINT      | AAdds a constraint after a table is already created        |
| ALL |  Returns true if all of the subquery values meet the condition      |   
| ALTER| Adds, deletes, or modifies columns in a table, or changes the data type of a column in a table |
| ALTER COLUMN | 	Changes the data type of a column in a table |
| ALTER TABLE| Adds, deletes, or modifies columns in a table |
| AND | Only includes rows where both conditions is true |
| ANY | Returns true if any of the subquery values meet the condition|
| AS |Renames a column or table with an alias|
| ASC | Sorts the result set in ascending order |
| BACKUP DATABASE | Creates a back up of an existing database|
| CASE |	Creates different outputs based on conditions|
|CHECK|	A constraint that limits the value that can be placed in a column|
|COLUMN|	Changes the data type of a column or deletes a column in a table|
|CONSTRAINT|	Adds or deletes a constraint|
|CREATE|	Creates a database, index, view, table, or procedure|
|CREATE DATABASE|	Creates a new SQL database|
|CREATE INDEX|	Creates an index on a table (allows duplicate values)|
|CREATE OR REPLACE VIEW|	Updates a view|
|CREATE TABLE	|Creates a new table in the database|
|CREATE PROCEDURE|	Creates a stored procedure|
|CREATE UNIQUE INDEX|	Creates a unique index on a table (no duplicate values)|
|CREATE VIEW	|Creates a view based on the result set of a SELECT statement|
|DATABASE|	Creates or deletes an SQL database|
|DEFAULT	|A constraint that provides a default value for a column|
|DELETE	|Deletes rows from a table|
|DESC|	Sorts the result set in descending order|
|DISTINCT	|Selects only distinct (different) values|
|DROP|	Deletes a column, constraint, database, index, table, or view|
|DROP COLUMN|	Deletes a column in a table|
|DROP CONSTRAINT|	Deletes a UNIQUE, PRIMARY KEY, FOREIGN KEY, or CHECK constraint|
|DROP DATABASE|	Deletes an existing SQL database|
|DROP DEFAULT|	Deletes a DEFAULT constraint|
|DROP INDEX	|Deletes an index in a table|
|DROP TABLE	|Deletes an existing table in the database|
|DROP VIEW|	Deletes a view|
|EXEC|	Executes a stored procedure|
|EXISTS	|Tests for the existence of any record in a subquery|
|FOREIGN KEY	|A constraint that is a key used to link two tables together|
|FROM|	Specifies which table to select or delete data from|
|FULL OUTER JOIN	|Returns all rows when there is a match in either left table or right table|
|GROUP BY|	Groups the result set (used with aggregate functions: COUNT, MAX, MIN, SUM, AVG)|
|HAVING|	Used instead of WHERE with aggregate functions|
|IN	|Allows you to specify multiple values in a WHERE clause|
|INDEX|	Creates or deletes an index in a table|
|INNER JOIN|	Returns rows that have matching values in both tables|
|INSERT INTO|	Inserts new rows in a table|
|INSERT INTO |SELECT	Copies data from one table into another table|
|IS NULL	|Tests for empty values|
|IS NOT NULL|	Tests for non-empty values|
|JOIN	|Joins tables|
|LEFT JOIN	|Returns all rows from the left table, and the matching rows from the right table|
|LIKE|	Searches for a specified pattern in a column|
|LIMIT|	Specifies the number of records to return in the result set|
|NOT|	Only includes rows where a condition is not true|
|NOT NULL|	A constraint that enforces a column to not accept NULL values|
|OR|	Includes rows where either condition is true|
|ORDER BY|	Sorts the result set in ascending or descending order|
|OUTER JOIN|	Returns all rows when there is a match in either left table or right table|
|PRIMARY KEY|	A constraint that uniquely identifies each record in a database table|
|PROCEDURE	|A stored procedure|
|RIGHT JOIN|	Returns all rows from the right table, and the matching rows from the left table|
|ROWNUM	|Specifies the number of records to return in the result set|
|SELECT|	Selects data from a database|
|SELECT DISTINCT|	Selects only distinct (different) values|
|SELECT INTO|	Copies data from one table into a new table|
|SELECT TOP	|Specifies the number of records to return in the result set|
|SET	|Specifies which columns and values that should be updated in a table|
|TABLE|	Creates a table, or adds, deletes, or modifies columns in a table, or deletes a table or data inside a table|
|TOP|	Specifies the number of records to return in the result set|
|TRUNCATE TABLE|	Deletes the data inside a table, but not the table itself|
|UNION|	Combines the result set of two or more SELECT statements (only distinct values)|
|UNION ALL	|Combines the result set of two or more SELECT statements (allows duplicate values)|
|UNIQUE|	A constraint that ensures that all values in a column are unique|
|UPDATE|	Updates existing rows in a table|
|VALUES	|Specifies the values of an INSERT INTO statement|
|VIEW|	Creates, updates, or deletes a view|
|WHERE|	Filters a result set to include only records that fulfill a specified condition|
