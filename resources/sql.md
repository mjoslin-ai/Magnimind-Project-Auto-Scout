# Magnimind


## Database
* Core Definition: A database is an organized collection of interrelated data designed to model a specific organization or process for a particular purpose.

* Data Types: It can store structured data (traditional facts like names and phone numbers) and unstructured data (modern content like tweets, photos, and documents).

* Purpose: Its primary goal is to turn raw, "useless" data into meaningful information by putting it into a context that increases a user's knowledge.

* Management: Databases are operated by a Database Management System (DBMS), which is the software used to create, update, store, and retrieve the data systematically.


## Relational Database
* Tables (Relations): The main structures in a database, each representing a single, specific subject.

* Columns (Attributes/Fields): The smallest structure that stores data; it represents a characteristic of the table's subject.

* Rows (Tuples/Records): Represents a unique instance of the subject, composed of the entire set of columns in that table.

* Primary Keys: One or more columns that uniquely identify each row within a table. 
    * A Composite Primary Key is a key made of two or more columns.
    * Primary keys enforce table-level integrity.

* Foreign Keys: A copy of a primary key from one table inserted into a second table to establish a relationship between them, often marked with an asterisk (*).


## SQL
* Definition: SQL stands for Structured Query Language. It is a programming language used to define, manipulate, and control data.

* Syntax Rules: While syntax can vary slightly between vendors, the basic rules include:

    * Case Insensitivity: SQL statements are not case-sensitive.

    * Formatting: New line characters are ignored.

    * Termination: Statements are terminated with a semicolon (;).

* Popular Systems: Common databases that utilize SQL include MySQL, PostgreSQL, Oracle, Microsoft SQL Server, and Access.


## Cardinality
* Definition: Cardinality refers to the maximum number of times a single row of data in one table can relate to instances in another table.


## SQL Statements
### SELECT 
Identifies the columns (attributes) you want to retrieve.

* Derived column: new column that is a combination of existing columns

* Concatenating two columns: SELECT firstName || ‘ ‘ || lastName as fullName

* DISTINCT: provides unique rows for all columns in the SELECT statement and only used once

### FROM 
Specifies the table(s) where the data is located.

* JOIN: Combines rows from two or more tables based on a related column (foreign key).
    * JOIN & ON: The ON clause matches a primary key from one table to a foreign key in another

    * INNER JOIN: matches values in both tables

    * LEFT JOIN: Returns all records from the left table, and the matched records from the right table.

    * RIGHT JOIN: The opposite of a Left Join. It returns all records from the right table, and the matched records from the left table. Any missing matches from the left side result in NULL values.

    * FULL JOIN: Returns all records when there is a match in either the left or right table. It essentially combines the results of both Left and Right joins. It will show NULL for whichever side is missing a match.

    * SELF JOIN: A self join is a regular join, but the table is joined with itself. This is useful for querying hierarchical data within a single table, such as a list of employees where one column contains the ID of their manager (who is also an employee in that same table).

### WHERE 
Filters the data based on specific conditions (e.g., Price > 100).

* LIKE
* IN
* NOT
* AND & BETWEEN
* OR

* IS NULL / IS NOT NULL: Occurs from missing data and often used in LEFT or RIGHT JOIN

* EXIST: Use EXISTS when your only interest is whether the subquery returns a nonempty set, and you don’t care what is in the set.

### GROUP BY 
Arranges identical data into groups (often used with functions like SUM or COUNT).

Any column that is not within an aggregation must show up in your GROUP BY statement.

### HAVING 
Filters groups created by the GROUP BY clause (similar to WHERE, but for groups). 

Used in place of WHERE on an element created by aggregation.

### ORDER BY 
Sorts the resulting data in ascending or descending order.

### LIMIT 
Restricts the number of rows returned in the result.

* OFFSET


## Aggregate Functions
A function where the values of multiple rows are grouped together as input on certain criteria to form a single value of more significant meaning.

These functions ignore NULL values and aggregate vertically

* COUNT(): Can be used on both numerical and non-numerical columns

* SUM(): 

* MIN() and MAX(): Can be used on non-numerical columns

* AVG(): returns mean of the data

* MEDIAN: difficult thing to get using SQL alone

* DATE_TRUNC(): Precision is down to the second


## Subqueries
A subquery is a query nested inside another query that can return:

* A single value (scalar subquery)

* A single row or single column (vector subquery)

* Or an entire table (table subquery)

In many cases, either a subquery or a join can be used to achieve the exact same result.


## Window Functions
Windows Function takes many rows and returns the same number of rows. Unlike aggregate functions which returns a single total, windows function shows the result next to every original row.

The most practical application of Window functions is to create a running total.

* PARTITION BY: Divides the rows into separate groups (partitions) so that the window function is applied independently to each group.

Unlike GROUP BY, which collapses rows and returns only one row per group, PARTITION BY keeps all original rows intact while still allowing calculations to be performed separately on each partition.

* LAG(): Used to compare the values of the current and the previous rows

* LEAD(): Used to compare the value of the current row with following row


## CASE
SQL's way of doing if, then, else logic