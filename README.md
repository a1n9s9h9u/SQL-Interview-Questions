## SQL Interview Questions

#### SQL EQUI JOIN

SQL EQUI JOIN performs a JOIN against equality or matching column(s) values of the associated tables. An equal sign (=) is used as comparison operator in the where clause to refer equality. You may also perform EQUI JOIN by using JOIN keyword followed by ON keyword and then specifying names of the columns along with their associated tables to check equality.
```sql
SELECT column_list 
FROM table1, table2....
WHERE table1.column_name =
table2.column_name; 

SELECT *
FROM table1 
JOIN table2
[ON (join_condition)]
```
An equijoin is a join with a join condition containing an equality operator. An equijoin returns only the rows that have equivalent values for the specified columns. An inner join is a join of two or more tables that returns only those rows (compared using a comparison operator) that satisfy the join condition.

#### RANK(), DENSE_RANK(), ROW_NUMBER()

RANK() gives you the ranking within your ordered partition. Ties are assigned the same rank, with the next ranking(s) skipped. So, if you have 3 items at rank 2, the next rank listed would be ranked 5.

DENSE_RANK() again gives you the ranking within your ordered partition, but the ranks are consecutive. No ranks are skipped if there are ranks with multiple items.

ROW_NUMBER() attributes a unique value to each row.

#### LAG()

The LAG() function allows access to a value stored in a different row above the current row. The row above may be adjacent or some number of rows above, as sorted by a specified column or set of columns.
```sql
id	seller_name	sale_value
3	Stef	7000
1	Alice	12000
2	Mili	25000

SELECT seller_name, sale_value,
  LAG(sale_value) OVER(ORDER BY sale_value) as previous_sale_value
FROM sale;

seller_name	sale_value	previous_sale_value
Stef	7000	NULL
Alice	12000	7000
Mili	25000	12000
```
#### LEAD()

LEAD() is similar to LAG(). Whereas LAG() accesses a value stored in a row above, LEAD() accesses a value stored in a row below.
```sql
SELECT seller_name, sale_value,
  LEAD(sale_value) OVER(ORDER BY sale_value) as next_sale_value
FROM sale;

seller_name	sale_value	next_sale_value
Stef	7000	12000
Alice	12000	25000
Mili	25000	NULL
```
#### Database

A database is an organized collection of data, stored and retrieved digitally from a remote or local computer system. A table is an organized collection of data stored in the form of rows and columns. Columns can be categorized as vertical and rows as horizontal. The columns in a table are called fields while the rows can be referred to as records.

#### DBMS

DBMS stands for Database Management System. DBMS is a system software responsible for the creation, retrieval, updation, and management of the database. It ensures that our data is consistent, organized, and is easily accessible by serving as an interface between the database and its end-users or application software.

#### RDBMS

RDBMS stands for Relational Database Management System. The key difference here, compared to DBMS, is that RDBMS stores data in the form of a collection of tables, and relations can be defined between the common fields of these tables. Most modern database management systems like MySQL, Microsoft SQL Server, Oracle, IBM DB2, and Amazon Redshift are based on RDBMS.

#### Structured Query Language

SQL stands for Structured Query Language. It is the standard language for relational database management systems. It is especially useful in handling organized data comprised of entities (variables) and relations between different entities of the data.

#### Constraints

Constraints are used to specify the rules concerning data in the table. It can be applied for single or multiple fields in an SQL table during the creation of the table or after creating using the ALTER TABLE command. The constraints are:

NOT NULL - Restricts NULL value from being inserted into a column.

CHECK - Verifies that all values in a field satisfy a condition.

DEFAULT - Automatically assigns a default value if no value has been specified for the field.

UNIQUE - Ensures unique values to be inserted into the field.

INDEX - Indexes a field providing faster retrieval of records.

PRIMARY KEY - Uniquely identifies each record in a table.

FOREIGN KEY - Ensures referential integrity for a record in another table.

#### PRIMARY KEY

The PRIMARY KEY constraint uniquely identifies each row in a table. It must contain UNIQUE values and has an implicit NOT NULL constraint. A table in SQL is strictly restricted to have one and only one primary key, which is comprised of single or multiple fields (columns).

#### FOREIGN KEY

A FOREIGN KEY comprises of single or collection of fields in a table that essentially refers to the PRIMARY KEY in another table. Foreign key constraint ensures referential integrity in the relation between two tables. The table with the foreign key constraint is labeled as the child table, and the table containing the candidate key is labeled as the referenced or parent table.

#### SQL Join

The SQL Join clause is used to combine records (rows) from two or more tables in a SQL database based on a related column between the two.

#### Self JOIN

A self JOIN is a case of regular join where a table is joined to itself based on some relation between its own column(s). Self-join uses the INNER JOIN or LEFT JOIN clause and a table alias is used to assign different names to the table within the query.
```sql
SELECT A.emp_id AS "Emp_ID",A.emp_name AS "Employee",
B.emp_id AS "Sup_ID",B.emp_name AS "Supervisor"
FROM employee A, employee B
WHERE A.emp_sup = B.emp_id;
```
#### Cross join

Cross join can be defined as a cartesian product of the two tables included in the join. The table after join contains the same number of rows as in the cross-product of the number of rows in the two tables. If a WHERE clause is used in cross join then the query will work like an INNER JOIN.
```sql
SELECT stu.name, sub.subject 
FROM students AS stu
CROSS JOIN subjects AS sub;
```
#### Index

A database index is a data structure that provides a quick lookup of data in a column or columns of a table. It enhances the speed of operations accessing data from a database table at the cost of additional writes and memory to maintain the index data structure.
```sql
CREATE INDEX index_name   /* Create Index */
ON table_name (column_1, column_2);
DROP INDEX index_name;   /* Drop Index */
```
Unique indexes are indexes that help maintain data integrity by ensuring that no two rows of data in a table have identical key values. Non-unique indexes, on the other hand, are not used to enforce constraints on the tables with which they are associated.

#### Clustered vs Non-clustered indexes

Clustered indexes are indexes whose order of the rows in the database corresponds to the order of the rows in the index. This is why only one clustered index can exist in a given table, whereas, multiple non-clustered indexes can exist in the table. The only difference between clustered and non-clustered indexes is that the database manager attempts to keep the data in the database in the same order as the corresponding keys appear in the clustered index.

#### Data Integrity

Data Integrity is the assurance of accuracy and consistency of data over its entire life-cycle and is a critical aspect of the design, implementation, and usage of any system which stores, processes, or retrieves data. It also defines integrity constraints to enforce business rules on the data when it is entered into an application or a database.

#### Query

A query is a request for data or information from a database table or combination of tables. A database query can be either a select query or an action query.
```sql
SELECT fname, lname    /* select query */
FROM myDb.students
WHERE student_id = 1;

UPDATE myDB.students    /* action query */
SET fname = 'Captain', lname = 'America'
WHERE student_id = 1;
```
#### Subquery

A subquery is a query within another query, also known as a nested query or inner query. It is used to restrict or enhance the data to be queried by the main query, thus restricting or enhancing the output of the main query respectively.
```sql
SELECT name, email, mob, address
FROM myDb.contacts
WHERE roll_no IN (
 SELECT roll_no
 FROM myDb.students
 WHERE subject = 'Maths');
```
#### SQL clauses

Some common SQL clauses used in conjuction with a SELECT query are as follows:

WHERE clause in SQL is used to filter records that are necessary, based on specific conditions.

ORDER BY clause in SQL is used to sort the records based on some field(s) in ascending (ASC) or descending order (DESC).
The UNION operator combines and returns the result-set retrieved by two or more SELECT statements.

The MINUS operator in SQL is used to remove duplicates from the result-set obtained by the second SELECT query from the result-set obtained by the first SELECT query and then return the filtered results from the first.

The INTERSECT clause in SQL combines the result-set fetched by the two SELECT statements where records from one match the other and then returns this intersection of result-sets.

#### Cursor

A database cursor is a control structure that allows for the traversal of records in a database. Cursors, in addition, facilitates processing after traversal, such as retrieval, addition, and deletion of database records. They can be viewed as a pointer to one row in a set of rows.

#### Entity

Entity: An entity can be a real-world object, either tangible or intangible, that can be easily identifiable. For example, in a college database, students, professors, workers, departments, and projects can be referred to as entities.

#### Relationships

Relationships: Relations or links between entities that have something to do with each other. For example - The employee's table in a company's database can be associated with the salary table in the same database.

One-to-One - This can be defined as the relationship between two tables where each record in one table is associated with the maximum of one record in the other table.

One-to-Many & Many-to-One - This is the most commonly used relationship where a record in a table is associated with multiple records in the other table.

Many-to-Many - This is used in cases when multiple instances on both sides are needed for defining a relationship.

Self-Referencing Relationships - This is used when a table needs to define a relationship with itself.

#### Alias

An alias is a feature of SQL that is supported by most, if not all, RDBMSs. It is a temporary name assigned to the table or table column for the purpose of a particular SQL query. In addition, aliasing can be employed as an obfuscation technique to secure the real names of database fields. A table alias is also called a correlation name. An alias is represented explicitly by the AS keyword but in some cases, the same can be performed without it as well. Nevertheless, using the AS keyword is always a good practice.

#### View

A view in SQL is a virtual table based on the result-set of an SQL statement. A view contains rows and columns, just like a real table. The fields in a view are fields from one or more real tables in the database.

#### Normalization vs Denormalization

Normalization represents the way of organizing structured data in the database efficiently. It includes the creation of tables, establishing relationships between them, and defining rules for those relationships. Inconsistency and redundancy can be kept in check based on these rules, hence, adding flexibility to the database.

Denormalization is the inverse process of normalization, where the normalized schema is converted into a schema that has redundant information. The performance is improved by using redundancy and keeping the redundant data consistent. The reason for performing denormalization is the overheads produced in the query processor by an over-normalized structure.

#### First normal form

A relation is in first normal form if every attribute in that relation is a single-valued attribute. If a relation contains a composite or multi-valued attribute, it violates the first normal form.

#### Second normal form

A relation is in second normal form if it satisfies the conditions for the first normal form and does not contain any partial dependency. A relation in 2NF has no partial dependency, i.e., it has no non-prime attribute that depends on any proper subset of any candidate key of the table. Often, specifying a single column Primary Key is the solution to the problem.

#### Third normal form

A relation is said to be in the third normal form, if it satisfies the conditions for the second normal form and there is no transitive dependency between the non-prime attributes, i.e., all non-prime attributes are determined only by the candidate keys of the relation and not by any other non-prime attribute.

#### Boyce-Codd Normal Form

A relation is in Boyce-Codd Normal Form if satisfies the conditions for third normal form and for every functional dependency, Left-Hand-Side is super key. In other words, a relation in BCNF has non-trivial functional dependencies in form X –> Y, such that X is always a super key.

#### DELETE, TRUNCATE, DROP

DELETE statement is used to delete rows from a table.

TRUNCATE command is used to delete all the rows from the table and free the space containing the table.

DROP command is used to remove an object from the database. If you drop a table, all the rows in the table are deleted and the table structure is removed from the database.

#### Aggregate function

An aggregate function performs operations on a collection of values to return a single scalar value. Aggregate functions are often used with the GROUP BY and HAVING clauses of the SELECT statement. Following are the widely used SQL aggregate functions:

AVG() - Calculates the mean of a collection of values.

COUNT() - Counts the total number of records in a specific table or view.

MIN() - Calculates the minimum of a collection of values.

MAX() - Calculates the maximum of a collection of values.

SUM() - Calculates the sum of a collection of values.

FIRST() - Fetches the first element in a collection of values.

LAST() - Fetches the last element in a collection of values.

#### Scalar function

A scalar function returns a single value based on the input value. Following are the widely used SQL scalar functions:

LEN() - Calculates the total length of the given field (column).

UCASE() - Converts a collection of string values to uppercase characters.

LCASE() - Converts a collection of string values to lowercase characters.

MID() - Extracts substrings from a collection of string values in a table.

#### User-defined functions

The user-defined functions in SQL are like functions in any other programming language that accept parameters, perform complex calculations, and return a value. They are written to use the logic repetitively whenever required.
```sql
CREATE FUNCTION east_or_west (
	@long DECIMAL(9,6)
)
RETURNS CHAR(4) AS
BEGIN
	DECLARE @return_value CHAR(4);
	SET @return_value = 'same';
    IF (@long > 0.00) SET @return_value = 'east';
    IF (@long < 0.00) SET @return_value = 'west';
 
    RETURN @return_value
END;
```
#### OLTP vs OLAP

OLTP stands for Online Transaction Processing, is a class of software applications capable of supporting transaction-oriented programs. An essential attribute of an OLTP system is its ability to maintain concurrency. To avoid single points of failure, OLTP systems are often decentralized. These systems are usually designed for a large number of users who conduct short transactions. Database queries are usually simple, require sub-second response times, and return relatively few records.

OLAP stands for Online Analytical Processing, a class of software programs that are characterized by the relatively low frequency of online transactions. Queries are often too complex and involve a bunch of aggregations. For OLAP systems, the effectiveness measure relies highly on response time. Such systems are widely used for data mining or maintaining aggregated, historical data, usually in multi-dimensional schemas.

#### Collation

Collation refers to a set of rules that determine how data is sorted and compared. Rules defining the correct character sequence are used to sort the character data. It incorporates options for specifying case sensitivity, accent marks, kana character types, and character width. Case sensitivity: A and a are treated differently.

#### Stored procedure

A stored procedure is a subroutine available to applications that access a relational database management system (RDBMS). Such procedures are stored in the database data dictionary. The sole disadvantage of stored procedure is that it can be executed nowhere except in the database and occupies more memory in the database server. It also provides a sense of security and functionality as users who can't access the data directly can be granted access via stored procedures.

A stored procedure that calls itself until a boundary condition is reached, is called a recursive stored procedure. This recursive function helps the programmers to deploy the same set of code several times as and when required.
```sql
CREATE PROCEDURE SelectAllCustomers
AS
SELECT * FROM Customers
GO;
```
#### Creating empty tables with the same structure

Creating empty tables with the same structure can be done smartly by fetching the records of one table into a new table using the INTO operator while fixing a WHERE clause to be false for all records.
```sql
SELECT * INTO Students_copy
FROM Students WHERE 1 = 2;
```
#### Pattern matching

SQL pattern matching provides for pattern search in data if you have no clue as to what that word should be. This kind of SQL query uses wildcards to match a string pattern, rather than writing the exact word. The LIKE operator is used in conjunction with SQL Wildcards to fetch the required information.

The % wildcard matches zero or more characters of any type and can be used to define wildcards both before and after the pattern.
```sql
SELECT *
FROM students
WHERE first_name LIKE 'K%'
```
The _ wildcard matches exactly one character of any type. It can be used in conjunction with % wildcard. This query fetches all students with letter K at the third position in their first name.
```sql
SELECT *
FROM students
WHERE first_name LIKE '__K%'
```
#### CTE (common table expression)

The CTE (common table expression), also known as the WITH clause, is an SQL feature that returns a temporary data set that can be used by another query. As it’s a temporary result, it’s not stored anywhere, but it still can be referenced like you would reference any other table.

A recursive CTE references itself. It returns the result subset, then it repeatedly (recursively) references itself, and stops when it returns all the results. Finding Bosses and Hierarchical Level for All Employees

![image](https://user-images.githubusercontent.com/97865583/195966630-0b402eb1-2f6c-4d95-a365-59dc8df4ac90.png)

```sql
WITH RECURSIVE company_hierarchy AS (
  SELECT    id,
            first_name,
            last_name,
            boss_id,
        0 AS hierarchy_level
  FROM employees
  WHERE boss_id IS NULL
 
  UNION ALL
   
  SELECT    e.id,
            e.first_name,
            e.last_name,
            e.boss_id,
        hierarchy_level + 1
  FROM employees e, company_hierarchy ch
  WHERE e.boss_id = ch.id
)
 
SELECT   ch.first_name AS employee_first_name,
       ch.last_name AS employee_last_name,
       e.first_name AS boss_first_name,
       e.last_name AS boss_last_name,
       hierarchy_level
FROM company_hierarchy ch
LEFT JOIN employees e
ON ch.boss_id = e.id
ORDER BY ch.hierarchy_level, ch.boss_id;
```
#### Dynamic SQL

Dynamic SQL is a programming technique that enables you to build SQL statements dynamically at runtime. You can create more general purpose, flexible applications by using dynamic SQL because the full text of a SQL statement may be unknown at compilation. Using dynamic SQL to query from any table example
```sql
DECLARE 
    @table NVARCHAR(128),
    @sql NVARCHAR(MAX);

SET @table = N'production.products';

SET @sql = N'SELECT * FROM ' + @table;

EXEC sp_executesql @sql;
```
#### Materialized View

Views are generally used when data is to be accessed infrequently and data in table get updated on frequent basis. On other hand Materialized Views are used when data is to be accessed frequently and data in table not get updated on frequent basis. A Materialized View persists the data returned from the view definition query and automatically gets updated as data changes in the underlying tables. It improves the performance of complex queries (typically queries with joins and aggregations) while offering simple maintenance operations.

#### Window functions

Window functions applies aggregate and ranking functions over a particular window (set of rows). OVER clause is used with window functions to define that window.
```sql
SELECT Name, Age, Department, Salary, 
AVERAGE(Salary) OVER( PARTITION BY Department ORDER BY Age) AS Avg_Salary
FROM employee
```
#### Ranking Window Functions :
```sql
SELECT 
ROW_NUMBER() OVER (PARTITION BY Department ORDER BY Salary DESC) 
AS emp_row_no, Name,  Department, Salary,
RANK() OVER(PARTITION BY Department 
ORDER BY Salary DESC) AS emp_rank,
DENSE_RANK() OVER(PARTITION BY Department 
                  ORDER BY Salary DESC) 
                  AS emp_dense_rank,
FROM employee 
```
#### Implementing Slowly Changing Dimensions (SCDs)

Slowly Changing Dimensions in Data Warehouse is an important concept that is used to enable the historic aspect of data in an analytical system. As you know, the data warehouse is used to analyze historical data, it is essential to store the different states of data. In data warehousing, we have fact and dimension tables to store the data. Dimensional tables are used to analyze the measures in the fact tables. In a data environment, data is initiated at operational databases and data will be extracted-transformed-loaded (ETL) to the data warehouse to suit the analytical environment.

#### SCD Type 0

There are situations where you ignore any changes. For example, when an employee joined an organization, there are joined related attributes such as joined Designation and JoinedDate, etc. that should not change over time. This is the example for Type 0 of Slowly Changing Dimensions in Data Warehouse.

![image](https://user-images.githubusercontent.com/97865583/195966675-ebe65cc8-86c9-4559-b212-f509201b3226.png)

#### SCD Type 1

In the Type 1 SCD, you simply overwrite data in dimensions. There can be situations where you don’t have the entire data when the record is initiated in the dimension. For example, when the customer record is initiated, you may not get all attributes. Therefore, when the customer record is initiated at the operational database, there will be empty or null records in the customer records. Once the ETL is executed, those empty records will be created in the data warehouse. Once these attributes are filled in the operational databases, that has to be updated in the data warehouse. Type 1 SCDs are identifying if the existing attributes are null and you are receiving a value from the operational table.

![image](https://user-images.githubusercontent.com/97865583/195966693-f3e8da7a-05a0-4c0a-82cf-01efbf1f50f6.png)

#### SCD Type 2

Type 2 Slowly Changing Dimensions in Data warehouse is the most popular dimension that is used in the data warehouse. As we discussed data warehouse is used for data analysis. If you need to analyze data, you need to accommodate historical aspects of data. Let us see how we can implement SCD Type 2. For the SCD Type 2, we need to include three more attributes such as StartDate, EndDate and IsCurrent.

![image](https://user-images.githubusercontent.com/97865583/195966698-047e2ec1-a924-46f4-ba89-005df92bbbbb.png)

In the above customer dimension, there are two records and let us say that customer whose CustomerCode is AW00011012, has been promoted to Senior Management. However, if you simply update the record with the new value, you will not see the previous records. Therefore, a new record will be created with a new CustomerKey and a new Designation. However, other attributes will be remaining the same.

![image](https://user-images.githubusercontent.com/97865583/195966705-af235c56-b8d7-4f7e-9cd5-f2bcba43fdcd.png)

#### SCD Type 3

Type 3 Slowly Changing Dimension in Data warehouse is a simple implementation where history will be kept in the additional column. If we relate the same scenario that we discussed under Type 2 SCD to Type 3 SCD, the customer dimension would look like below.

![image](https://user-images.githubusercontent.com/97865583/195966709-30b19d55-bac6-440c-be0c-c679880d00e6.png)

#### SCD Type 4

As we discussed in SCD type 2, we maintain the history by adding a different version of the row to the dimension. However, if the changes are rapid in nature Type 2 SCD will not be scalable. SCD Type 4 is introduced in order to fix this issue. In this technique, a rapidly changing column is moved out of the dimension and is moved to a new dimension table. This new dimension is linked to the fact table.

#### SCD Type 6

Type 6 Slowly Changing Dimensions in Data Warehouse is a combination of Type 2 and Type 3 SCDs. This means that Type 6 SCD has both columns are rows in its implementation.

![image](https://user-images.githubusercontent.com/97865583/195966718-6fa09718-7358-4bd4-b5c8-25f94322654d.png)

#### What Is Skewness?

Skewness refers to a distortion or asymmetry that deviates from the normal distribution, in a set of data. For example, India has more than 50% of its population below the age of 25 and more than 65% below the age of 35. If you’ll plot the distribution of the age of the population of India, you will find that there is a hump on the left side of distribution and the right side is comparatively planar. In other words, we can say that there’s a skew towards the end.

#### LISTAGG

LISTAGG function in DBMS is used to aggregate strings from data in columns in a database table.
```sql
SUBNO      SUBNAME
---------- ------------------------------
D20        Algorithm
D30        DataStructure
D30        C
D20        C++
D30        Python
D30        DBMS
D10        LinkedList
D20        Matrix
D10        String
D30        Graph
D20        Tree

SELECT SubNo, LISTAGG(SubName, ' , ') WITHIN GROUP (ORDER BY SubName) AS SUBJECTS FROM GfG GROUP BY SubNo;
```
#### Pivot and Unpivot in SQL

In SQL, Pivot and Unpivot are relational operators that are used to transform one table into another in order to achieve more simpler view of table. Conventionally we can say that Pivot operator converts the rows data of the table into the column data. The Unpivot operator does the opposite that is it transform the column based data into rows.

![image](https://user-images.githubusercontent.com/97865583/195966804-2807f20c-ebb9-45ed-8073-e69dcf0a81bb.png)
```sql
SELECT CourseName, PROGRAMMING, INTERVIEWPREPARATION
FROM geeksforgeeks 
PIVOT 
( 
SUM(Price) FOR CourseCategory IN (PROGRAMMING, INTERVIEWPREPARATION ) 
) AS PivotTable 

SELECT CourseName, CourseCategory, Price 
FROM 
(
SELECT CourseName, PROGRAMMING, INTERVIEWPREPARATION FROM geeksforgeeks 
PIVOT 
( 
SUM(Price) FOR CourseCategory IN (PROGRAMMING, INTERVIEWPREPARATION) 
) AS PivotTable
) P 
UNPIVOT 
( 
Price FOR CourseCategory IN (PROGRAMMING, INTERVIEWPREPARATION)
) 
AS UnpivotTable
```
#### How to display Cumulative Total in SQL ?
```sql
CREATE TABLE dbo.DataValues
 (ID INT,
 [VALUE] INT
 )

 INSERT INTO  DataValues
 (ID, [VALUE])
 VALUES
 (1, 25),
 (2, 20),
 (3, 75),
 (4, 20),
 (5, 15),
 (6, 120)

SELECT ID, [VALUE], 
SUM([VALUE]) OVER (ORDER BY ID) AS [RUNNING TOTAL]
FROM dbo.DataValues
```
#### NTILE()

NTILE() function in SQL Server is a window function that distributes rows of an ordered partition into a pre-defined number of roughly equal groups. It assigns each group a number_expression ranging from 1. NTILE() function assigns a number_expression for every row in a group, to which the row belongs.
```sql
ID
1
2
3
4
5
6
7
8
9
10
```
Use NTILE() function to divide above rows into 3 groups :
```sql
SELECT ID,
NTILE (3) OVER (
ORDER BY ID
) Group_number
FROM geeks_demo; 

ID	Group_number
1	1
2	1
3	1
4	1
5	2
6	2
7	2
8	3
9	3
10	3
```
#### DDL, DML, DCL, TCL, and DQL

Data Definition Language (DDL): DDL changes the structure of the table like creating a table, deleting a table, altering a table, etc. Here are some commands that come under DDL:
```sql
CREATE
ALTER
DROP
TRUNCATE
```
Data Manipulation Language: DML commands are used to modify the database. It is responsible for all form of changes in the database. Here are some commands that come under DML:
```sql
INSERT
UPDATE
DELETE
```
Data Control Language: DCL commands are used to grant and take back authority from any database user. Here are some commands that come under DCL:
```sql
Grant
Revoke
```
Transaction Control Language: TCL commands can only use with DML commands like INSERT, DELETE and UPDATE only. These operations are automatically committed in the database that's why they cannot be used while creating tables or dropping them. Here are some commands that come under TCL:
```sql
COMMIT
ROLLBACK
SAVEPOINT
```
Data Query Language: DQL is used to fetch the data from the database. It uses only one command:
```sql
SELECT
```
#### Order of SQL execution

From and Joins
Where
Group By
Having
Select
Distinct
Order By
Limit

#### Vertical vs Horizontal scaling

Scaling alters the size of a system. In the scaling process, we either compress or expand the system to meet the expected needs. The scaling operation can be achieved by adding resources to meet the smaller expectation in the current system, or by adding a new system in the existing one, or both.

Vertical scaling keeps your existing infrastructure but adds computing power. Your existing pool of code does not need to change — you simply need to run the same code on machines with better specs. By scaling up, you increase the capacity of a single machine and increase its throughput. Vertical scaling allows data to live on a single node, and scaling spreads the load through CPU and RAM resources for your machines.

Horizontal scaling simply adds more instances of machines without first implementing improvements to existing specifications. By scaling out, you share the processing power and load balancing across multiple machines.

#### Sharding

Sharding is a method of splitting and storing a single logical dataset in multiple databases. By distributing the data among multiple machines, a cluster of database systems can store larger dataset and handle additional requests. Sharding is necessary if a dataset is too large to be stored in a single database. Moreover, many sharding strategies allow additional machines to be added. Sharding allows a database cluster to scale along with its data and traffic growth.

#### SQL Keys

A key is a set of attributes that can identify each tuple uniquely in the given relation. Types of Keys:

Super Key – A superkey is a set of attributes that can identify each tuple uniquely in the given relation. A super key may consist of any number of attributes.

Candidate Key – A set of minimal attribute(s) that can identify each tuple uniquely in the given relation is called a candidate key.

Primary Key – A primary key is a candidate key that the database designer selects while designing the database. Primary Keys are unique and NOT NULL.

Alternate Key – Candidate keys that are left unimplemented or unused after implementing the primary key are called alternate keys.

Foreign Key – An attribute ‘X’ is called as a foreign key to some other attribute ‘Y’ when its values are dependent on the values of attribute ‘Y’. The relation in which attribute ‘Y’ is present is called the referenced relation. The relation in which attribute ‘X’ is present is called the referencing relation.

Composite Key – A primary key composed of multiple attributes and not just a single attribute is called a composite key.

Unique Key – It is unique for all the records of the table. Once assigned, its value cannot be changed i.e. it is non-updatable. It may have a NULL value.
Normalization is the process of organizing data by disintegrating bigger table into smaller one’s with proper dependencies. Redundant Data wastes a lot of disk space and creates maintenance problems (Update, Insert and Delete Anomaly). Hence the DB tables should be Normalized.

#### Functional dependency

A functional dependency is a constraint that specifies the relationship between two sets of attributes where one set can accurately determine the value of other sets. It is denoted as X → Y, where X is a set of attributes that is capable of determining the value of Y. The attribute set on the left side of the arrow, X is called Determinant, while on the right side, Y is called the Dependent.

#### ER model

ER model stands for an Entity-Relationship model. It is a high-level data model. This model is used to define the data elements and relationship for a specified system. It develops a conceptual design for the database. It also develops a very simple and easy to design view of data. In ER modelling, the database structure is portrayed as a diagram called an entity-relationship diagram.

#### Serializability

Serializability is a concept that helps us to check which schedules are serializable. A serializable schedule is the one that always leaves the database in consistent state.

#### Concurrency Control

Concurrency Control is the management procedure that is required for controlling concurrent execution of the operations that take place on a database. The concurrency control protocols ensure the atomicity, consistency, isolation, durability and serializability of the concurrent execution of the database transactions.

#### Entity type

The entity type is a collection of the entity having similar attributes. Types of Entity type:

Strong Entity Type:Strong entities are those entity types which have a key attribute. The primary key helps in identifying each entity uniquely. It is represented by a rectangle.

Weak Entity Type: Weak entity type doesn’t have a key attribute. Weak entity types can’t be identified on their own. It depends upon some other strong entity for its distinct identity.

#### Entity Set

Entity Set: Entity Set is a collection of entities of the same entity type. We can say that entity type is a superset of the entity set as all the entities are included in the entity type.

#### Why count(*) should not be used in Production environment? 

Ans) It creates a lot of stress while computing this query. When we use * it means the Sql engine has to consider all rows/records which is much more time consuming. So, instead we must use Count(1) which uses Sql indexes to compute which is much more faster than using Count(*).
