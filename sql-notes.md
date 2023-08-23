### Data cleaning involves  
- Remove duplicate or irrelevant observations - Get rid of repeating or unrelated data  
- Fix structural errors - Correct naming or formatting mistakes  
- Filter unwanted outliers - Remove unusual or irrelevant data points  
- Handle missing data - Deal with information that is not available  
- Validate and QA - Test and check data for accuracy  


## What are some optimization techniques in SQL?
- Build indexes. Using indexes on a table, It will dramatically increase the performance of your read operation because it will allow you to perform index scan or index seek depending on your search predicates and select predicates instead of table scan.
Building non-clustered indexes, you could also increase the performance further.

- You could also use an indexed view, which is a way to create one or more clustered indexes on the same table.
In that way, the query optimizer will consider even the clustered keys on the indexed views so there might be a possible faster option to execute your query.

- Do table partitioning. When a particular table has a billion of records, it would be practical to partition a table so that it can increase the read operation performance. Every partitioned
table will be considered as physical smaller tables internally.  

- Use stored procedures because when you first execute a stored procedure, its execution plan is stored and the
same execution plan will be used for the subsequent executions rather than generating an execution plan every
time.

- Use the 3 or 4 naming conventions. If you use the 2 naming convention, table name and column name, the SQL engine will take some time to find its schema. By specifying the schema name or
even server name, you will be able to save some time for the SQL server.

- Avoid using SELECT *. Because you are selecting everything, it will decrease the performance. Try to select columns you need.

- Avoid using CURSOR because it is an object that goes over a table on a row-by-row basis, which is similar to the table scan. It is not really an effective way.

- Avoid using unnecessary TRIGGER. If you have unnecessary triggers, they will be triggered needlessly. Not only slowing the performance down, it might mess up your whole program as well.

- Try to use JOIN instead of SET operators or SUB-QUERIES because set operators and sub- queries are slower than joins and you can implement the features of sets and sub-queries using joins.

- Avoid using LIKE operators, which is a string matching operator but it is mighty slow. 

- Avoid using blocking operations such as order by or derived columns.

## What are the differences between OLTP and OLAP?

- OLTP stands for Online Transactional Processing 
- OLAP stands for Online Analytical Processing

OLTP:
Normalization Level: highly normalized  
Data Usage : Current Data (Database)  
Processing : fast for delta operations (DML)  
Operation : Delta operation (update, insert, delete) aka DML Terms Used : Table, columns and relationships  

OLAP:  
Normalization Level: highly denormalized Data Usage : historical Data (Data warehouse) Processing : fast for read operations Operation : read operation (select)  
Terms Used : dimension table, fact table

## What are the different database objects ?

There are total seven database objects (6 permanent database object + 1 temporary database object) Permanent DB objects  

- Table
- Views
- Stored procedures
- User-defined Functions
- Triggers
- Indexes Temporary DB object 
- Cursors

## What is Normalization?

- Step by step process to reduce the degree of data redundancy.

- Breaking down one big flat table into multiple table based on normalization rules. Optimizing the memory but not in term of performance.

- Normalization will get rid of insert, update and delete anomalies.

- Normalization will improve the performance of the delta operation (aka. DML operation); UPDATE, INSERT, DELETE

- Normalization will reduce the performance of the read operation; SELECT

What are the three degrees of normalization and how is normalization done in each degree?

1NF:
A table is in 1NF when: 
- All the attributes are single-valued.

- With no repeating columns (in other words, there cannot be two different columns with the same information).

- With no repeating rows (in other words, the table must have a primary key). All the composite attributes are broken down into its minimal component.

- There should be SOME (full, partial, or transitive) kind of functional dependencies between non-key and key attributes.

- 99% of times, it’s usually 1NF.

2NF:
A table is in 2NF when: 
- It is in 1NF.
- There should not be any partial dependencies so they must be removed if they exist.

3NF:
A table is in 3NF when:  
- It is in 2NF.

- There should not be any transitive dependencies so they must be removed if they exist.

BCNF:
- A stronger form of 3NF so it is also known as 3.5NF

- We do not need to know much about it. Just know that here you compare between a prime attribute and a prime attribute and a non-key attribute and a non-key attribute.

## What is the SQL server query execution sequence?

- FROM -> goes to Secondary files via primary file
- WHERE -> applies filter condition (non-aggregate column) 
- SELECT -> dumps data in tempDB system database  
- GROUP BY -> groups data according to grouping predicate 
- HAVING -> applies filter condition (aggregate function) 
- ORDER BY -> sorts data ascending/descending

## What is the difference between UNION and UNION ALL?

UNION: 
The UNION command is used to select related information from two tables, much like the JOIN command. However, when using the UNION command all selected columns need to be of the same data type. With UNION, only distinct values are selected.

UNION ALL: 
The UNION ALL command is equal to the UNION command, except that UNION ALL selects all values.

## What is a view in SQL? How to create one

A view is a virtual table based on the result-set of an SQL statement. We can create using create view syntax.  

CREATE VIEW view_name AS  
SELECT column_name(s)  
FROM table_name  
WHERE condition  

## What are the uses of view?

1. Views can represent a subset of the data contained in a table; consequently, a view can limit the degree of exposure of the underlying tables to the outer world: a given user may have permission to query the view, while denied access to the rest of the base table.  
   
2. Views can join and simplify multiple tables into a single virtual table  

3. Views can act as aggregated tables, where the database engine aggregates data (sum, average etc.) and presents the calculated results as part of the data  

4. Views can hide the complexity of data; for example a view could appear as Sales2000 or Sales2001, transparently partitioning the actual underlying table  

5. Depending on the SQL engine used, views can provide extra security

## What is the difference between “Primary Key” and “Unique Key”?

1. We can have only one Primary Key in a table whereas we can have more than one Unique Key in a table.

2. The Primary Key cannot have a NULL value whereas a Unique Key may have only one null value.

3. By default, a Primary Key is a Clustered Index whereas by default, a Unique Key is a unique non-clustered index.

4. A Primary Key supports an Auto Increment value whereas a Unique Key doesn't support an Auto Increment value.

## What is the difference between the “WHERE” clause and the “HAVING” clause?

1. WHERE clause can be used with a Select, Update and Delete Statement Clause but the HAVING clause can be used only with a Select statement.

2. We can't use an aggregate functions in the WHERE clause unless it is in a sub-query contained in a HAVING clause whereas we can use an aggregate function in the HAVING clause. We can use a column name in the HAVING clause but the column must be contained in the group by clause.

3. WHERE is used before the GROUP BY clause whereas a HAVING clause is used to impose a condition on the GROUP Function and is used after the GROUP BY clause in the query.

4. A WHERE clause applies to each and every row whereas a HAVING clause applies to summarized rows (summarized with GROUP BY).

5. In the WHERE clause the data that is fetched from memory depending on a condition whereas in HAVING the completed data is first fetched and then separated depending on the condition.

## What is the difference between the “DELETE” and “TRUNCATE” SQL commands?

1. The DELETE command is used to remove rows from a table based on a WHERE condition whereas TRUNCATE removes all rows from a table.

2. So we can use a where clause with DELETE to filter and delete specific records whereas we cannot use a Where clause with TRUNCATE.

3. DELETE is executed using a row lock, each row in the table is locked for deletion whereas TRUNCATE is executed using a table lock and the entire table is locked for removal of all records.

4. DELETE is a DML command whereas TRUNCATE is a DDL command.

5. DELETE retains the identity of the column value whereas in TRUNCATE, the Identify
column is reset to its seed value if the table contains any identity column.

6. To use Delete you need DELETE permission on the table whereas to use Truncate on
a table you need at least ALTER permission on the table.

7. DELETE uses more transaction space than the TRUNCATE statement whereas
Truncate uses less transaction space than DELETE statement.

8. DELETE can be used with indexed views whereas TRUNCATE cannot be used with
indexed views.

9. The DELETE statement removes rows one at a time and records an entry in the
transaction log for each deleted row whereas TRUNCATE TABLE removes the data by deallocating the data pages used to store the table data and records only the page deallocations in the transaction log.

10. Delete activates a trigger because the operation is logged individually whereas TRUNCATE TABLE can't activate a trigger because the operation does not log individual row deletions.

## Joins in SQL

https://drive.google.com/file/d/14Lh0R5nZfJp9gFTHUxmiXiBLfy702T3K/view?usp=sharing

## What is SQL?

Answer: SQL (Structured Query Language) is a programming language used to manage and manipulate relational databases.

## What are the main types of SQL commands?

Answer: SQL commands are mainly of four types: Data Definition Language (DDL), Data Manipulation Language (DML), Data Control Language (DCL), and Transaction Control Language (TCL).

## How would you retrieve all records from a table?

Answer: Use the SELECT statement: "SELECT * FROM table_name;"

## What is the difference between INNER JOIN and OUTER JOIN?

Answer: INNER JOIN returns matching rows, while OUTER JOIN returns matching rows and non-matching rows from one or both tables.

## Explain GROUP BY clause.

Answer: GROUP BY groups rows based on specified columns, and you can use aggregate functions like COUNT, SUM, AVG, etc., with it.

## How to filter results in SQL?

Answer: Use the WHERE clause: "SELECT * FROM table_name WHERE condition;"

## What is the purpose of the HAVING clause?

Answer: The HAVING clause filters grouped results based on specified conditions, similar to the WHERE clause but used with GROUP BY.

## How would you sort query results?

Answer: Use the ORDER BY clause: "SELECT * FROM table_name ORDER BY column_name;"

## Explain the concept of a primary key.

Answer: A primary key uniquely identifies each record in a table and ensures data integrity by preventing duplicate or null values.

## What is a subquery?

Answer: A subquery is a query nested within another query and is used to return data for the outer query.

## How would you update data in a table?

Answer: Use the UPDATE statement: "UPDATE table_name SET column_name = new_value WHERE condition;"

## What is the purpose of the UNION operator?

Answer: UNION combines the result sets of two or more SELECT queries into a single result set, removing duplicates by default.

## How would you delete data from a table?

Answer: Use the DELETE statement: "DELETE FROM table_name WHERE condition;"

## Explain the concept of an index.

Answer: An index improves query performance by creating a quick access path to data, much like an index in a book.

## What is normalization in SQL?

Answer: Normalization is the process of organising data in a database to minimize redundancy and dependency issues.

## How to calculate the average of a column?

Answer: Use the AVG function: "SELECT AVG(column_name) FROM table_name;"

## What is the purpose of the CASE statement?

Answer: The CASE statement allows you to perform conditional logic in SQL queries, similar to the if-else construct in other programming languages.

## Explain the ACID properties of transactions.

Answer: ACID stands for Atomicity, Consistency, Isolation, and Durability. It ensures database transactions are reliable and maintains data integrity.

## How to find the highest value in a column?

Answer: Use the MAX function: "SELECT MAX(column_name) FROM table_name;"

## What is a foreign key?

Answer: A foreign key establishes a link between two tables, referencing the primary key of another table to maintain referential integrity.

## How do you count the number of rows in a table?

Answer: Use the COUNT function: "SELECT COUNT(*) FROM table_name;"

## Explain the difference between CHAR and VARCHAR data types.

Answer: CHAR is a fixed-length string, while VARCHAR is a variable-length string. VARCHAR uses only the space required for the data.

## What is a self-join?

Answer: A self-join is a type of SQL join where a table is joined with itself based on a related column.

## How to add a new column to an existing table?

Answer: Use the ALTER TABLE statement: "ALTER TABLE table_name ADD new_column datatype;"

## What are stored procedures?

Answer: Stored procedures are precompiled SQL code stored in the database that can be executed with a single call, providing modularity and security.

## can you explain the difference between union and union all? 

One gives all results, one gives a unique set of results. Also, I'm not a fan of select *. It is fine for development work but should never hit production in my opinion...
