------
PHP Data Objects (PDO)
-------
PHP Data Objects (PDO) is the class that connects to the database and allows you to
interact with it. This is the popular way to work with databases for PHP developers,
even though there are other ways that we will not discuss here. PDO allows you
to work with different database systems, so you are not tied to MySQL only. In the
following sections, we will consider how to connect to a database, insert data, and
retrieve it using this class.

## Connecting to the database
One of the formats for MySQL databases is <database type>:host=<host>;dbname
=<schema name> . As our database system is MySQL, it runs on the same server, and
the schema name is bookstore , DSN will be mysql:host=127.0.0.1;dbname=book
store . Let's take a look at how we will put everything together:

```
$dbConfig = Config::getInstance()->get('db');
$db = new PDO(
'mysql:host=127.0.0.1;dbname=bookstore',
$dbConfig['user'],
$dbConfig['password']
);
$db->setAttribute(PDO::ATTR_DEFAULT_FETCH_MODE, PDO::FETCH_ASSOC);
```
Note also that we will invoke the setAttribute method from the PDO instance.
This method allows you to set some options to the connection; in this case, it sets
the format of the results coming from MySQL. This option forces MySQL to return
the arrays whose keys are the names of the fields, which is way more useful than
the default one, returning numeric keys based on the order of the fields. Setting this
option now will affect all the queries performed with the $db instance, rather than
setting the option each time we perform a query.

## Performing queries
```
$rows = $db->query('SELECT * FROM book ORDER BY title');
foreach ($rows as $row) {
var_dump($row);
}
```

## Prepared statements
Variables usually come from the user side and can contain malicious code. It is
always better to first sanitize these values. PDO provides the ability to prepare a statement—that is, a query that is
parameterized. You can specify parameters for the fields that will change in the
query and then assign values to these parameters. Let's consider first an example,
as follows:
```
$query = 'SELECT * FROM book WHERE author = :author';
$statement = $db->prepare($query);
$statement->bindValue('author', 'George Orwell');
$statement->execute();
$rows = $statement->fetchAll();
var_dump($rows);
```
Here these three function are :
•	 bindValue : This takes two arguments: the name of the parameter as
described in the query and the value to assign. If you provide a parameter
name that is not in the query, this will throw an exception.
•	 execute : This will send the query to MySQL with the replacement of the
parameters by the provided values. If there is any parameter that is not
assigned to a value, the method will throw an exception. As its brother exec ,
execute will return a Boolean, specifying whether the query was executed
successfully or not.
•	 fetchAll : This will retrieve the data from MySQL in case it was a SELECT
query. As a query, fetchAll will return a list of all rows as arrays.


## Working with transactions
A transaction is a state where MySQL keeps track of all the changes that you make
in your data in order to be able to revert all of them if needed. You need to explicitly
start a transaction, and before you close the connection to the server, you need to
commit your changes. This means that MySQL does not really perform these changes
until you tell it to do so. If during a transaction you want to revert the changes, you
should roll back instead of making a commit.

PDO allows you to do this with three functions:
•	 beginTransaction : This will start the transaction.
•	 commit : This will commit your changes. Keep in mind that if you do not
commit and the PHP script finishes or you close the connection explicitly,
MySQL will reject all the changes you made during this transaction.
•	 rollBack : This will roll back all the changes that were made during this
transaction.
