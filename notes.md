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

1. UNION 
The UNION command is used to select related information from two tables, much like the JOIN command. However, when using the UNION command all selected columns need to be of the same data type. With UNION, only distinct values are selected.

2. UNION ALL 
The UNION ALL command is equal to the UNION command, except that UNION ALL selects all values.
