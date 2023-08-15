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
