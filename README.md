# SQL Reference
It is very compressed SQL Reference notes... It will be very useful while working with SQL(Structured Query Language). Checkout the below SQL reference without wasting your time.

--------------------------------------------------------------------------------------
                               SQL REFERENCE BOOK CUM CHEAT SHEET
--------------------------------------------------------------------------------------

# <center>STRUCTURED QUERY LANGUAGE(SQL)</center>
It is structured language designed to work with databases. It is used in individual
and co-operate server.

#### SQL accepted by the Databases are:
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

## To Create Database
Using below the command line you can create your database.
```
CREATE DATABASE databaseName;
```
## To Drop the Database
To delete the existing database use the following command:
```
DROP DATABASE databaseName;
```

## To Create the Table
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

### Insert Into Table
To insert the value in table use the below command line :
```
INSERT INTO tableName (colName1, colName2)
VALUES ('obj1', 'obj2' ),
('obj3', 'obj4' ),
('obj5', 'obj6' ),
('obj7', 'obj8' );    // that's how you can add multiple value in table.
```
### Update Into The Table
To update the value of any column use the following command line:
```
UPDATE tableName
SET colName = 'updatedValue'
WHERE id = 4;  // most important line otherwise whole column will be updated.
```

### Delete Value Into the Table
To Delete the any recored use the following command.
```
DELETE FROM tableName
WHERE id =4; // here id is used to delete that record which not required anymore.
```
## <center>Alter the Table(Make Changes in Table)</center>
