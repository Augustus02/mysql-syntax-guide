# MySQL Syntax guide

## Login into mysql from terminal using root

sudo mysql -u root -p

## Show users

SELECT user FROM mysql.user;

## Create user

CREATE USER 'new_user'@'localhost' IDENTIFIED BY 'user_password';

## Grant privileges

GRANT ALL PRIVILEGES ON database_name TO 'new_user'@'localhost';

## Show granted privileges

SHOW GRANTS FOR 'new_user'@'localhost';

## Remove privileges

REVOKE ALL PRIVILEGES ON new_user FROM 'new_user'@'localhost';

## Show all databases

SHOW DATABASES;

## Delete a database

DROP DATABASE database_name;

## create a database

CREATE DATABASE database_name;

## Select a database

USE database_name;

## Create a table with columns and their data types 

CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype
)

## Show tables

SHOW tables;

## Delete/Drop a table

DROP TABLE table_name

## How to insert a single row into a table

INSERT INTO table_name (column1, column2, column3) VALUES (value1, value2, value3);

## How to insert multiple rows into a table

INSERT INTO table_name (column1, column2, column3) VALUES
(value1, value2, value3),
(value1, value2, value3),
(value1, value2, value3);

## Select with the WHERE clause

SELECT * FROM table_name WHERE value1 = 1;

## Select with the WHERE clause using a range

The values can be integers or strings

SELECT * FROM table_name WHERE column_name BETWEEN value1 AND value2;

## Delete an individual row

You need to specify what row you are deleting using the value

DELETE FROM table_name WHERE value1 = value;

## How to UPDATE a row

You need to specify what row you are updating using the value

UPDATE table_name SET column1 = value1 WHERE value1 = value;

## How to add a new column to a table

ALTER TABLE table_name ADD column_name datatype;

## Order by using the DISTINCT clause

SELECT DISTINCT * FROM table_name ORDER BY column_name ASC;

## How to concatenate columns
CONCAT can display multiple strings and/or a columns values together

SELECT CONCAT(column_name," this is a string") AS test FROM table_name;

## How to select distinct rows

SELECT DISTINCT column1 FROM table_name;

## How to use LIKE to search
In the below example it will only display the values that start with v

SELECT * FROM table_name WHERE column_name LIKE 'v%';

## Select using the IN clause

SELECT * FROM table_name WHERE column_name IN (values);

## How to create an index
CREATE INDEX index_name ON table_name (column1, column2, ...);

## How to remove an index
DROP INDEX index_name ON table_name;

## Two tables demonstrating a one to many relationship that has a PK & FK

A customer can have multiple orders but an order can only have one customer.

CREATE TABLE customers (
    customerID INT,
    name VARCHAR(50),
    PRIMARY KEY (customerID)
);

CREATE TABLE orders (
    orderID INT,
    customerID,
    PRIMARY KEY (orderID),
    FOREIGN KEY (customerID) REFERENCES customers(customerID)
);

## Inner join

SELECT column_name(s) FROM table1 INNER JOIN table2 ON table1.column_name = table2.column_name;

## How to JOIN multiple tables

SELECT column_name(s) FROM ((table1 
INNER JOIN table1 ON table.column_name = table2.column_name)
INNER JOIN table1 ON table1.column_name = table3.column_name);
