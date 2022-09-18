
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

## **The SQL SELECT DISTINCT Statement**

The statement is used to return only different (different) values. SELECT DISTINCT
Within a table, a column often contains many duplicate values; and sometimes you just want to list the different (different) values.
For example: 
```
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
> Below is a selection from the "Customers" table in the Northwind sample database:

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

```
USE Northwind
Go

SELECT * FROM Customers 
WHERE ContactName = 'Hanna Moos' OR Country = 'Germany'
```

```
USE Northwind
GO

SElECT * FROM Customers WHERE NOT City = 'Berlin'
```

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

*  Order by value desc

```
USE Northwind
GO

SELECT LastName, FirstName, Address 
FROM Employees 
ORDER BY LastName DESC
```

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

## **SQL MIN and MAX functions()**

>* The **MIN()** function returns the smallest value of the selected column.
>* The **MAX()** function returns the largest value of the selected column.

MIN() Syntax
```
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```
```
SELECT MIN(Price) AS SmallestPrice
FROM Products;
```

MAX() Syntax
```
SELECT MAX(Price) AS LargestPrice
FROM Products;
```
```
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```
## **SQL COUNT(), AVG() and SUM() Functions**

The SQL COUNT(), AVG() and SUM() Functions
The COUNT() function returns the number of rows that matches a specified criterion.

COUNT() Syntax

```
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

The AVG() function returns the average value of a numeric column.

AVG() Syntax
```
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```
The SUM() function returns the total sum of a numeric column. 

SUM() Syntax
```
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```
## **LIKE Operator**

The SQL LIKE Operator
The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

There are two wildcards often used in conjunction with the LIKE operator:

 >The percent sign (%) represents zero, one, or multiple characters
 >The underscore sign (_) represents one, single character
 >* Note: MS Access uses an asterisk (*) instead of the percent sign (%), and a question mark (?) instead of the underscore (_).

The percent sign and the underscore can also be used in combinations!
```
LIKE Syntax
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;
```
>* `Tip:` You can also combine any number of conditions using AND or OR operators.

Here are some examples showing different LIKE operators with '%' and '_' wildcards:

| **LIKE Operator**  | **Description**  | 
| :------------ |:--------------- |	
|WHERE CustomerName LIKE 'a% | Finds any values that start with "a"|
|WHERE CustomerName LIKE '%a'|	Finds any values that end with "a"|
|WHERE CustomerName LIKE '%or%'|	Finds any values that have "or" in any position|
|WHERE CustomerName LIKE '_r%'|	Finds any values that have "r" in the second position|
|WHERE CustomerName LIKE 'a_%'|	Finds any values that start with "a" and are at least 2 characters in length|
|WHERE CustomerName LIKE 'a__%'|	Finds any values that start with "a" and are at least 3 characters in length|
|WHERE ContactName LIKE 'a%o'	|Finds any values that start with "a" and ends with "o"|

## SQL Wildcards
**SQL Wildcard Characters**
A wildcard character is used to substitute one or more characters in a string.

Wildcard characters are used with the LIKE operator. The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

Wildcard Characters in MS Access
	
| **LIKE Symbol**  | **Description	Example**  | 
| :------------ |:--------------- |	
|*	Represents| zero or more characters	bl* finds bl, black, blue, and blob|
|?	Represents| a single character	h?t finds hot, hat, and hit|
|[]	Represents| any single character within the brackets	h[oa]t finds hot and hat, but not hit|
|!	Represents| any character not in the brackets	h[!oa]t finds hit, but not hot and hat|
|-	Represents| any single character within the specified range	c[a-b]t finds cat and cbt|
|#	Represents| any single numeric character 2#5 finds 205, 215, 225, 235, 245, 255, 265, 275, 285, and 295|

**Wildcard Characters in SQL Server**

| **LIKE Symbol**  | **Description	Example**  | 
| :------------ |:--------------- |	
|%	Represents |zero or more characters	bl% finds bl, black, blue, and blob|
|_	Represents |a single character	h_t finds hot, hat, and hit|
|[]	Represents |any single character within the brackets	h[oa]t finds hot and hat, but not hit|
|^	Represents |any character not in the brackets	h[^oa]t finds hit, but not hot and hat|
|-	Represents |any single character within the specified range	c[a-b]t finds cat and cbt|

All the wildcards can also be used in combinations!

Here are some examples showing different LIKE operators with '%' and '_' wildcards:

| **LIKE Symbol**  | **Description	Example**  | 
| :------------ |:--------------- |	
|WHERE CustomerName LIKE 'a%'	| Finds any values that starts with "a"                                                 |
|WHERE CustomerName LIKE '%a'	| Finds any values that ends with "a"|
|WHERE CustomerName LIKE '%or%'	| Finds any values that have "or" in any position|
|WHERE CustomerName LIKE '_r%'	| Finds any values that have "r" in the second position|
|WHERE CustomerName LIKE 'a__%'	| Finds any values that starts with "a" and are at least 3 characters in length|
|WHERE ContactName LIKE 'a%o'	| Finds any values that starts with "a" and ends with "o"|

Using the % Wildcard
The following SQL statement selects all customers with a City starting with "ber":

Example

```
SELECT * FROM Customers
WHERE City LIKE 'ber%';
```

The following SQL statement selects all customers with a City containing the pattern "es": 

Example
```
SELECT * FROM Customers
WHERE City LIKE '%es%';
```

Using the _ Wildcard
The following SQL statement selects all customers with a City starting with any character, followed by "ondon":

Example

```
SELECT * FROM Customers
WHERE City LIKE '_ondon';
```

The following SQL statement selects all customers with a City starting with "L", followed by any character, followed by "n", followed by any character, followed by "on":

Example

```
SELECT * FROM Customers
WHERE City LIKE 'L_n_on';
```

Using the [charlist] Wildcard
The following SQL statement selects all customers with a City starting with "b", "s", or "p":

Example

```
SELECT * FROM Customers
WHERE City LIKE '[bsp]%';
```

The following SQL statement selects all customers with a City starting with "a", "b", or "c":

Example
```
SELECT * FROM Customers
WHERE City LIKE '[a-c]%';
```

Using the [!charlist] Wildcard
The two following SQL statements select all customers with a City NOT starting with "b", "s", or "p":

Example
```
SELECT * FROM Customers
WHERE City LIKE '[!bsp]%';
```
## **SQL IN Operator**
The SQL IN Operator
The IN operator allows you to specify multiple values in a WHERE clause.

The IN operator is a shorthand for multiple OR conditions.

IN Syntax

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```
or:

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);
```
## **SQL BETWEEN Operator**
The SQL BETWEEN Operator
The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.

The BETWEEN operator is inclusive: begin and end values are included. 

BETWEEN Syntax

```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

## **SQL Aliases**

SQL aliases are used to give a table, or a column in a table, a temporary name.
Aliases are often used to make column names more readable.
An alias only exists for the duration of that query.
An alias is created with the AS keyword.

Alias Column Syntax

```
SELECT column_name AS alias_name
FROM table_name;
Alias Table Syntax
SELECT column_name(s)
FROM table_name AS alias_name;
```

**Alias for Columns Examples**

The following SQL statement creates two aliases, one for the CustomerID column and one for the CustomerName column:

```
Example
SELECT CustomerID AS ID, CustomerName AS Customer
FROM Customers;
```
The following SQL statement creates two aliases, one for the CustomerName column and one for the ContactName column. Note: It requires double quotation marks or square brackets if the alias name contains spaces:

Example

```
SELECT CustomerName AS Customer, ContactName AS [Contact Person]
FROM Customers;
```
The following SQL statement creates an alias named "Address" that combine four columns (Address, PostalCode, City and Country):

Example
```
SELECT CustomerName, Address + ', ' + PostalCode + ' ' + City + ', ' + Country AS Address
FROM Customers;
```
Note: To get the SQL statement above to work in MySQL use the following:

```
SELECT CustomerName, CONCAT(Address,', ',PostalCode,', ',City,', ',Country) AS Address
FROM Customers;
```
Note: To get the SQL statement above to work in Oracle use the following:
```
SELECT CustomerName, (Address || ', ' || PostalCode || ' ' || City || ', ' || Country) AS Address
FROM Customers;
Alias for Tables Example
```
The following SQL statement selects all the orders from the customer with CustomerID=4 (Around the Horn). We use the "Customers" and "Orders" tables, and give them the table aliases of "c" and "o" respectively (Here we use aliases to make the SQL shorter):

```
SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName='Around the Horn' AND c.CustomerID=o.CustomerID;
```

The following SQL statement is the same as above, but without aliases:
```
SELECT Orders.OrderID, Orders.OrderDate, Customers.CustomerName
FROM Customers, Orders
WHERE Customers.CustomerName='Around the Horn' AND Customers.CustomerID=Orders.CustomerID;
```

## **SQL Joins**

A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

Let's look at a selection from the "Orders" table:


| OrderID  | CustomerID  | OrderDate |
| :------------ |:---------------:| -----:|
|10308	|2	|1996-09-18|
|10309	|37|	1996-09-19|
|10310	|77|	1996-09-20|

Then, look at a selection from the "Customers" table:

| CustomerID  | CustomerName  | ContactName |Country |
| :------------ |:---------------| :---------|:---------|
|1	       |  Alfreds Futterkiste	      |              Maria Anders|	Germany|
|2	       |Ana Trujillo Emparedados y helados	  |  Ana Trujillo	|Mexico|
|3       	|Antonio Moreno Taquería	              |  Antonio Moreno| 	Mexico|

**Notice that the "CustomerID" column in the "Orders" table refers to the "CustomerID" in the "Customers" table. The relationship between the two tables above is the "CustomerID" column.**

Then, we can create the following SQL statement (that contains an INNER JOIN), that selects records that have matching values in both tables:

Example
```
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```

and it will produce something like this:

| OrderID  | CustomerName  | OrderDate |
| :------------ |:---------------:| -----:|
|10308|	Ana Trujillo  Emparedados y helados	|9/18/1996 |
|10365|	Antonio Moreno Taquería	            |11/27/1996|
|10383|	Around the Horn	                    |12/16/1996|
|10355|	Around the Horn	                    |11/15/1996|
|10278|	Berglunds snabbköp	                |8/12/1996|

>Different Types of SQL JOINs
>Here are the different types of the JOINs in SQL:

* (INNER) JOIN: Returns records that have matching values in both tables
* LEFT (OUTER) JOIN: Returns all records from the left table, and the matched records from the right table
* RIGHT (OUTER) JOIN: Returns all records from the right table, and the matched records from the left table
* FULL (OUTER) JOIN: Returns all records when there is a match in either left or right table

![INNERS](https://user-images.githubusercontent.com/76973247/190918352-c3c29836-8167-44b0-a650-481f97f9f5ed.png)

## **SQL INNER JOIN Keyword**

The INNER JOIN keyword selects records that have matching values in both tables.

INNER JOIN Syntax

```
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

In this tutorial we will use the well-known Northwind sample database.

Below is a selection from the "Orders" table:

| OrderID  | CustomerID  | EmployeeID |OrderDateShipperID|
| :------------ |:---------------| :--------|:---------------| 
|10308|	2	|7	|1996-09-18	|3|
|10309|	37|	3|	1996-09-19|	1|
|10310|	77|	8|	1996-09-20|	2|

And a selection from the "Customers" table:

|CustomerID	|CustomerName	|ContactName|	Address	|City|	PostalCode	|Country|
| :------------ |:---------------| :--------|:---------------|:---------------|  :--------|:---------------| 
|1  | Alfreds Futterkiste 	|Maria Anders|	Obere Str. 57	|Berlin|	12209	|Germany|
|2|Ana Trujillo  Emparedados y helados	|Ana Trujillo|	Avda. de la Constitución 2222	|México D.F.	|05021	|Mexico|
|3	|Antonio Moreno  Taquería	|Antonio Moreno|	Mataderos 2312	|México D.F.	|05023	|Mexico|


SQL INNER JOIN Example
The following SQL statement selects all orders with customer information:

Example
```
SELECT Orders.OrderID, Customers.CustomerName
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```
>Note: The INNER JOIN keyword selects all rows from both tables as long as there is a match between the columns. If there are records in the "Orders" table that do not have matches in "Customers", these orders will not be shown!

JOIN Three Tables
The following SQL statement selects all orders with customer and shipper information:

Example

```
SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
FROM ((Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);
```
## **SQL LEFT JOIN Keyword**

The LEFT JOIN keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.

LEFT JOIN Syntax:

```
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
Note: In some databases LEFT JOIN is called LEFT OUTER JOIN.
```

In this tutorial we will use the well-known Northwind sample database.

Below is a selection from the "Customers" table:

|CustomerID	|CustomerName	|ContactName|	Address	|City|	PostalCode	|Country|
| :------------ |:---------------| :--------|:---------------|:---------------|  :--------|:---------------| 
|1   |Alfreds Futterkiste  	|Maria Anders	|Obere Str. 57	|Berlin	|12209|	Germany|
|2   |Ana Trujillo Emparedados y helados |	Ana Trujillo|	Avda. de la Constitución 2222	|México D.F.	|05021|	Mexico|
|3	|Antonio Moreno Taquería	|Antonio Moreno|	Mataderos |2312	México D.F.	|05023|	Mexico|

And a selection from the "Orders" table:

|OrderID	|CustomerID	|EmployeeID	|OrderDate	|ShipperID	|
| :------------ | :------------ | :------------ | :------------ | :------------ |
|10308|	2	|7	|1996-09-18	|3|
|10309	|37	|3	|1996-09-19	|1|
|10310	|77	|8	|1996-09-20	|2|

SQL LEFT JOIN Example
The following SQL statement will select all customers, and any orders they might have:

Example

```
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
ORDER BY Customers.CustomerName;
```
## **SQL RIGHT JOIN Keyword**
The RIGHT JOIN keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match.

RIGHT JOIN Syntax

```
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;

```
Note: In some databases RIGHT JOIN is called RIGHT OUTER JOIN.

SQL RIGHT JOIN

Demo Database
In this tutorial we will use the well-known Northwind sample database.

Below is a selection from the "Orders" table:

| OrderID  | CustomerID  | EmployeeID | OrderDate |ShipperID |
| :------------ |:---------------:| -----:|-----:|-----:|
|10308|	2	|7	|1996-09-18	|3|
|10309|	37|	3|	1996-09-19|	1|
|10310|	77|	8|	1996-09-20|	2|

And a selection from the "Employees" table:

| EmployeeID  | LastName  | FirstName | BirthDate |Photo |
| :------------ |:---------------:| -----:|-----:|-----:|
|1|	Davolio	Nancy	|12/8/1968|	EmpID1.pic|
|2|	Fuller	Andrew	|2/19/1952|	EmpID2.pic|
|3|	Leverling	Janet|	8/30/1963	|EmpID3.pic|


SQL RIGHT JOIN Example
The following SQL statement will return all employees, and any orders they might have placed:

Example

```
SELECT Orders.OrderID, Employees.LastName, Employees.FirstName
FROM Orders
RIGHT JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
ORDER BY Orders.OrderID;
Note: The RIGHT JOIN keyword returns all records from the right table (Employees), even if there are no matches in the left table (Orders).
```
SQL FULL OUTER JOIN Keyword
The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right (table2) table records.

Tip: FULL OUTER JOIN and FULL JOIN are the same.

FULL OUTER JOIN Syntax
```
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```

## **SQL FULL OUTER JOIN Keyword**
The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right (table2) table records.

Tip: FULL OUTER JOIN and FULL JOIN are the same.

FULL OUTER JOIN Syntax
```
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```

SQL FULL OUTER JOIN

>Note: FULL OUTER JOIN can potentially return very large result-sets!

Demo Database
In this tutorial we will use the well-known Northwind sample database.

Below is a selection from the "Customers" table:

|CustomerID|	CustomerName|	ContactName	|Address|	City|	PostalCode|	Country|
| :------------ |:---------------|:---------------|:---------------|:---------------|:---------------|:---------------|
|1| Alfreds Futterkiste	|Maria Anders|	Obere Str. 57|	Berlin|	12209|	Germany|
|2|	Ana Trujillo Emparedados y helados	|Ana Trujillo|	Avda. de la Constitución 2222|	México D.F.|	05021	|Mexico|
|3|	Antonio Moreno Taquería	|Antonio Moreno|	Mataderos 2312|	México D.F.|	05023	|Mexico|

And a selection from the "Orders" table:

|OrderID	|CustomerID|	EmployeeID|	OrderDate|	ShipperID|
| :------------ |:---------------|:---------------|:---------------|:---------------|
|10308|	2	|7	|1996-09-18	|3|
|10309|	37|	3|	1996-09-19|	1|
|10310|	77|	8|	1996-09-20|	2|

SQL FULL OUTER JOIN Example
The following SQL statement selects all customers, and all orders:

```
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;
```

A selection from the result set may look like this:

|CustomerName	|OrderID          | 
| :------------ |:---------------:|
|Null	|10309|
|Null	|10310|
|Alfreds Futterkiste|	Null|
|Ana Trujillo Emparedados y helados|	10308|
|Antonio Moreno Taquería|	Null|

>Note: The FULL OUTER JOIN keyword returns all matching records from both tables whether the other table matches or not. So, if there are rows in "Customers" that do not have matches in "Orders", or if there are rows in "Orders" that do not have matches in "Customers", those rows will be listed as well.

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
