# SQL REFFERENCE BOOK
It is very compressed SQL Reference notes... It will be very useful while working with SQL(Structured Query Language).
Checkout the below SQL reference without wasting your time.

<strong>Love From My Keyboard :-)</strong>

--------------------------------------------------------------------------------------
                               SQL REFERENCE BOOK CUM CHEAT SHEET
--------------------------------------------------------------------------------------

## DATABASE :
Database is a software which is used to store the data and make operations on it using
SQL(structure Query Language). basically database is devided into two parts :

![database_Type](/databasetype.png);

### TO USE THE MYSQL
In order to use the mysql for handling relational database you should first need to
install two things:
![mysql_install](/mysql_install.png);

### SCHEMA
Relational database systems store data in different databases or schemas, which separate
the data from different applications. These schemas are just collections of tables. In
every Server's They have their own schema basically what it is... it is matadata of the server.
You should do not make change in server schema but you can create your own schema. So these are
some useful commands:

#### CREATE SCHEMA
syntax:
```
CREATE SCHEMA bookstore(schama_name);
```

#### USE SCHEMA
Syntax:
```
USE bookstore(schema_name);
```
#### SHOW SCHEMA
If you do not remember what the name of your schema is or want to check which
other schemas are in your server, you can run the SHOW SCHEMAS;
```
SHOW SCHEMAS
```

#### USEFUL IMAGES
![numType](/numType.png)

![datefun](/dateFun.png)

# <center>STRUCTURED QUERY LANGUAGE(SQL)</center>
It is structured language designed to work with databases. It is used in individual
and co-operate server.

#### SQL COMMAND BASED DATABASE ARE:
1. MYSQL
2. ORACLE
3. SQLite
4. Hadoop
5. MS SQL SERVER
6. OPENBASE

#### TOOLS TO WORK WITH SQL
1. Command Line Command(Black screen).
2. Adminer
3. Phpmyadmin
4. MYSQL (My Sql Workbench).  //popular
5. Sequel Pro(Mac).
-------------------------------------------------------------------------------------------



## TO CREATE THE DATABASE
Using below the command line you can create your database.
```
CREATE DATABASE databaseName;
```
## TO DROP THE DATABASE
To delete the existing database use the following command:
```
DROP DATABASE databaseName;
```
-------------------------------------------------------------------------------------------



## TO CREATE THE TABLE
To create the table in existing database such as databaseName. Follow the below command.

```
CREATE TABLE tableName(
  id INT NOT NULL AUTO_INCREMENT,  // AUTO_INCREMENT will increment the value of id by 1.
  colName1 VARCHAR(255), // INT and  VARCHAR is datatype with following the size in parenthesis.
  colName2 DATE,
  PRIMARY KEY(id) // It will remains unique throughout the table
  );
```

### INSERT INTO THE TABLE
To insert the value in table use the below command line :
```
INSERT INTO tableName (colName1, colName2)
VALUES ('obj1', 'obj2' ),
('obj3', 'obj4' ),
('obj5', 'obj6' ),
('obj7', 'obj8' );    // that's how you can add multiple value in table.
```
### UPDATE INTO THE TABLE
To update the value of any column use the following command line:
```
UPDATE tableName
SET colName = 'updatedValue'
WHERE id = 4;  // most important line otherwise whole column will be updated.
```

### DELETE RECORD INTO THE TABLE
To Delete the any recored use the following command.
```
DELETE FROM tableName
WHERE id =4; // here id is used to delete that record which not required anymore.
```
---------------------------------------------------------------------------------------



## <center>Alter the Table(Make Changes in Table)</center>

### ADD A COLUMN IN TABLE
To add a column in existing table use the following command:
```
ALTER TABLE tableName
ADD newColName VARCHAR(255); // name followed by attributes.
```
### CHANGE THE DATATYPE OF ANY COLUMN
```
ALTER TABLE tableName
MODIFY COLUMN colName INT(11) // If modify not work use alter.
```

### DELETE A COLUMN
```
ALTER TABLE tableName
DROP COLUMN colName;
```
------------------------------------------------------------------------------------------



## SELECT QUERY ON COLUMN


### SELECT ALL COLUMN
To select all the column of your table use to following command:
```
SELECT * FROM tableName;
```

### SELECT SPECIFIC COLUMN
To select only the seeking column use the following command;
```
SELECT colName1, colName2 FROM tableName;
```
### SELECT ALL RECORD USING THE VALUE(Prefers id)
To select the record Which has the value given by user... use the following command:
```
SELECT * FROM tableName
WHERE id = 4;
```
### SELECT ALL RECORD ORDER BY SPECIFIC COLUMN
```
SELECT * FROM tableName
ORDER BY colName1 DES/ASC; // Descending and Ascending order.
```
### DISTINCT DATA FROM THE TABLE
```
SELECT DISTINCT colName FROM tableName;  // Use DISTINCT keyword.
```
-----------------------------------------------------------------------------------------------


## SQL OPERATORS

| OPERATOR       | EXAMPLE                    |
| :------------- | :-------------             |
| =              | name = "slowestwind"       |
| !=             | age != 20                  |
| >              | age > 20                   |
| <              | age<20                     |
| >=             | age>=20                    |
| <=             | age<=10                    |
| BETWEEN        | age BETWEEN 18 and 70      |
| LIKE           | firstName LIKE "name%"     |
| IN             | marks IN (55, 84, 95)      |
| IS OR IS NOT   | name IS NOT NULL           |
| AS             | SELECT name as lastName    |

### BETWEEN OPERATORS

```
SELECT * FROM tableName
WHERE age
BETWEEN 18 AND 70
```

### LIKE OPERATORS
It is used to match some kind of pattern in column. Here in %on, % stand for anything but but in the end 'on' must required.
```
SELECT * FROM tableName
Where name LIKE "%on";
```

### REGEX OPERATORS
It is pattern matching based on Regular Expression.
Pattern	What the pattern matches
- ^ 	Beginning of string
- $	  End of string
- .	  Any single character
- [...]	  Any character listed between the square brackets
- [^...]	 Any character not listed between the square brackets
- p1|p2|p3	 Alternation; matches any of the patterns p1, p2, or p3
- *	  Zero or more instances of preceding element
- +	  One or more instances of preceding element
- {n}	  n instances of preceding element
- {m,n}	  m through n instances of preceding element


```
SELECT * FROM tableName
Where name REGEXP '^s'; // return all data starting with char s
```

### IN OPERATOR
It is allows to multiple value in Where clause. Use the following command:
```
SELECT * FROM tableName
WHERE state IN ('NEW DELHI', 'MUMBAI');  // here we got all the recored which has city mention here.
```
------------------------------------------------------------------------------------



## INDEXES
Indexes can be created in table to find data more quickly and efficiently. You will not see the indexes but
you will see the speed up  of searches and queries. It used where you need to search values or item frequently, don't put everywhere.

### CREATE INDEX ON COLUMN
```
CREATE INDEX indexName
ON tableName(colName) ;   // colName is the column which we want to index.
```
### DROP/DELETE INDEX
Use command to Delete the index on the column.
```
DROP INDEX indexName
ON tableName(colName);  
```
-----------------------------------------------------------------------------------------



## RELATIONSHIPS AND FOREIGN KEYS

Database designs are closely related to database relationships, the association between two columns in one or more tables. Relationships are defined on the basis of matching key columns. In SQL server, these relationships are defined using Primary Key-Foreign Key constraints. A link is created between two tables where the primary key of one table is associated with the foreign key of another table using database relationships.

let's learn taking an example

<strong>This is customer table</strong>
```
CREATE TABLE databaseName.customer(
  id INT NOT NULL IDENTITY PRIMARY KEY,
  fName VARCHAR(255),
  lName VARCHAR(255)
  email VARCHAR(255),
  address VARCHAR(255)
  city VARCHAR(255),
  state VARCHAR(255)
  );
```

<strong>This is product table</strong>

```
CREATE TABLE databaseName.products(
  id INT NOT NULL IDENTITY PRIMARY KEY,
  name VARCHAR(255),
  price VARCHAR(255)
  );
```

<strong>This is orders table</strong>

```
CREATE TABLE databaseName.orders(
  id INT NOT NULL IDENTITY PRIMARY KEY,
  orderNumber INT(255),
  productId VARCHAR(255),
  customerId INT(255),
  age INT;
  orderDate DATETIME,
  FOREIGN KEY(customerId) REFERECES customers(id),
  FOREIGN KEY(productId) REFERECES product(id)
  );
```
---------------------------------------------------------------------------------------

## JOIN THE TABLES
Basically use to combine the records two or more table based on common field between them.
Join types are:



![joins](/joins.png);

- Inner Join,
- Left Join,
- Right Join,
- Full Join.

### INNER JOIN
Returns records that have matching values in both tables

<strong>Join two table</strong>
```
SELECT colName(s)
FROM tableName1
INNER JOIN tableName2
ON tableName1.colName = tableName2.colName;
```
<strong>Join three table</strong>
```
SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
FROM Orders
  INNER JOIN Customers
  	ON Orders.CustomerID = Customers.CustomerID)
  INNER JOIN Shippers
	ON Orders.ShipperID = Shippers.ShipperID
  );

```

### LEFT JOIN
The LEFT JOIN keyword returns all records from the tableName1, and the matched records from the tableName2.
The result is NULL from the right side, if there is no match.

```
SELECT colName(s)
FROM tableName1
LEFT JOIN tableName2
ON tableName1.colName = tableName2.colName;
```


### RIGHT JOIN
The RIGHT JOIN keyword returns all records from the tableName2, and the matched records from the tableName1.
The result is NULL from the left side, if there is no match.

```
SELECT colName(s)
FROM tableName1
RIGHT JOIN tableName2
ON tableName1.colName = tableName2.colName;
```

### FULL JOIN
Returns all records when there is a match in either left or right table

```
SELECT colName(s)
FROM tableName1
FULL OUTER JOIN tableName2
ON tableName1.colName = tableName2.colName;  /// most of the time we use id here...
WHERE condions;
```
---------------------------------------------------------------------------------------

# ALIASES

Aliases basically gives table's column a temporary names to it.

Syntax:
```
SELECT colName1 AS  'col Name1',
colName2 AS 'col Name2'  // Here the column heading will change.
FROM tableName;
```


## To CONCAT THE TABLE
syntax:
```
SELECT CONCAT(colName1,' ', colName2)
AS 'Name_to_Concat_Column'
FROM tableName;
```
## To SELECT from the Different columns
It will select column from different table.
syntax:
```
SELECT t1.id, t1.colName1, t2.colName1, t2.colName2
FROM tableName1 AS t1,  tableName2 AS t2;  //Here AS is used to change the table name
```
-------------------------------------------------------
 SQL AGGREGATE FUNCTIONS
-------------------------------------------------------
### AVERAGE FUNCTION
syntax:
```
SELECT AVG(colName)  // mention here colName which you want to find avg.
FROM tableName;
```

### COUNT FUNCTION
syntax:
```
SELECT COUNT(colName)
FROM tableName;
```
### MAXIMUM VALUE IN COLUMN
syntax:
```
SELECT MAX(colName)
FROM tableName;
```
### MINIMUM VALUE IN COLUMN
syntax:
```
SELECT MIN(colName)
FROM tableName;
```
### SUM OF VALUE IN COLUMN
syntax:
```
SELECT SUM(colName)
FROM tableName;
```
### GROUP BY FUNCTION
syntax:
```
SELECT colName,
COUNT(colName)
FROM tableName
WHERE colName>condition
GROUP BY colName;
```
### UPPERCASE IN COLUMN
syntax:
```
SELECT UCASE(colName)
FROM tableName;
```
### LOWERCASE IN COLUMN
syntax:
```
SELECT LCASE(colName)
FROM tableName;
```

### CASE FUNCTIONS
It is same as If then else funtion.
syntax:
```
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```
### CEIL FUNCTION
CEIL() function returns the smallest integer value that is bigger than or equal to a number.
```
SELECT CEIL(99.67); // it will return 100.
```
### RIGHT FUNCTION
RIGHT() function extracts a number of characters from a string (starting from right).
```
RIGHT(string, number_of_chars)

EXAMPLE:
SELECT RIGHT(CustomerName, 5) AS ExtractString
FROM Customers;
```
### ROUND() FUNCTION
Returs round figure of given number.
example:
```
SELECT round(number, Precision_digit)
SELECT round(7845.265474984, 2) // it will return 7845.26
```

### TRUNCATE() FUNCTION
TRUNCATE() function truncates a number to the specified number of decimal places.
example:
```
SELECT TRUNCATE(1354.3075, 2); // ans. 1354.30
```
### REVERSE() FUNCTION
REVERSE() function reverses a string and returns the result.
example:
```
REVERSE(string)
```

### TRIM() FUNCTION
Remove leading and trailing spaces from a string
example:
```
SELECT TRIM('    slowestwind    ') // returns only slowestwind without spaces.
```

### LIMIT
MySQL supports the LIMIT clause to select a limited number of records
example:
```
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```


--------------------------------------------------------------------
### DATE FUNCTIONS
---------------------------------------------------------------------
### ADDDATE() FUNCTION
DDDATE() function adds a time/date interval to a date and then returns the date.
example :
```
SELECT ADDDATE("2019-06-10", INTERVAL 10 DAY);
```

### CURDATE() FUNCTION
returns the current date.
example:
```
SELECT CURDATE();
```
### CURRENT_TIMESTAMP() FUNCTION
Returns current time and date.
example :
```
SELECT CURRENT_TIMESTAMP();
```

### DATEDIFF() FUNCTION
Returns the difference between two dates.
example:
```
DATEDIFF(date1, date2)
```
### EXTRACT() FUNCTION
It will returns part of day or time.
example:
```
SELECT EXTRACT(WEEK FROM "2017-06-15"); // extract week from day.

SELECT EXTRACT(YEAR_MONTH FROM "2017-06-15 09:34:21"); //year and month from date and time.

```
