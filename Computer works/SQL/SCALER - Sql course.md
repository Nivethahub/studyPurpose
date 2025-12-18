
1. Module:
   >  What is Database?
   > 	What is DBMS?
   > 	Types of Databases
   > 	RDBMS
   > 	Installation & setup
   
**Database**
A database is a collection of data stored in a format that can be easily accessed, managed and updated.

Why we need DB?
 Most applications require a database to store and retrieve data.
 
 A shopping website like Amazon will need a database to store data about customers, products, orders, suppliers etc.
 
 Know how to monitore and optimise your database is essential for the app performance.

How do you work with a database?
We couldn't directly interact with it. Bcz it might be little complicated or inconsistent data to interact

In order to avoid the issues like these, all the datas that stored in a database will be managed by Database Management System (DBMS).

**Database Management System**

Database management systems are software system used to manage and manipulate data in a database

A DBMS servers it is an interface between an endUser and a database, allowing users to CRUD operation in the database

**Types of Databases**

Relational Databases:
+ Also known as SQL database, which uses SQL language to queries the databases
+ It stores data in the form of tables
+ Each row in the table is a record with unique id called key
+ The columns of the table hold attributes of database
+ The relational data model provides a standard way of representing and querying data that could be used by any application.
+ SQL databases are vertically scalable
+ Track inventores, sales, banking, finance, billing, e-commerce

No-SQL Databases:
+ These databases have their own query language
+ It stores data in the form of documents, graph, timeseries, key-value etc
+ It was horizontally scalable
  
**MySQL**
+ Free and open source
+ Huge community support
+  Extensively tested
+ High stablility
+ Available for all major platforms
+ Replication and sharding are available
+ Covers a wide range of use cases
  

| Syntax   | UseCase                                           |     |
| -------- | ------------------------------------------------- | --- |
| Select   | To filter the columns                             |     |
| *        | To select all the datas without the conditions    |     |
| From     | Which table                                       |     |
| Where    | Filter the data or condition                      |     |
| ORDER BY | Sorting range like ascending descending like that |     |

  Example used Syntax for classicmodels:
  
  Dummy practice:
  1. Select * from classicmodels. Customers
  2. Select *  from employees 
     OR
      select * from classicmodels. Employees (if the use database not mentioned or not defaulty used)
  3. Select firstname, lastName from employees 
       [ firstname (as mentioned in Table column), lastName (as mentioned in Table column) ]    
   
   QUERY PART:
   
   >  Select Statement
   
   Select *
   From employees
   Where officeCode=1
   Order by firstName
   
   