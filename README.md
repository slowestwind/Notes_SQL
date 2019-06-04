# SQL REFFERENCE BOOK
It is very compressed SQL Reference notes... It will be very useful while working with SQL(Structured Query Language). Checkout the below SQL reference without wasting your time.

--------------------------------------------------------------------------------------
                               SQL REFERENCE BOOK CUM CHEAT SHEET
--------------------------------------------------------------------------------------



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
To create the table in existing database name such as databaseName just you have created using
the CREATE DATABASE.

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
CREATE TABLE databaseName.products(
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

<strong>This is orders0 table</strong>

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
  INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
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

## SQL AGGREGATE FUNCTIONS

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
