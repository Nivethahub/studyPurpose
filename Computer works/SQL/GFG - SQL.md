###  Introduction to Databases

Get introduced to the concept of databases, their types, and the career opportunities SQL offers.

- What is a Database?
- Types of Databases
- SQL Career Path: Roles, Skills & Salaries

###  Getting Started with SQL

Understand about SQL fundamentals and knowledge of Database Management Systems (DBMS).

- What is SQL?
- Introduction to DBMS (Database Management System)

### Setting Up SQL Environment

Learn to install and manage your SQL server and connect to it via command line.

- Install MySQL on Windows
- Start & Stop MySQL Server
- Connecting to MySQL Using Command Line Options

### Basic SQL Commands: DDL

Begin working with Data Definition Language (DDL) commands to create and modify database structures.

- CREATE and ALTER Commands
- DROP and TRUNCATE Commands
- SQL Data Types
- CREATE TABLE Statement

###  Basic SQL Commands: DML

Learn Data Manipulation Language (DML) commands to insert, update, and delete data in your tables.

- INSERT INTO Statement
- UPDATE Statement
- DELETE Statement

### Querying with SELECT

Start querying data using the SELECT statement and explore common clauses to filter and sort results.

- Basic SELECT Query
- SELECT DISTINCT
- Using Aliases
- WHERE Clause
- ORDER BY Clause

### SQL Operators

Explore various SQL operators to build more powerful and precise queries.

- Overview of SQL Operators
- Comparison Operators
- Logical Operators
- Arithmetic Operators


What is Database?

Data refers to raw, unorganised facts and figures such as numbers text images and symbols that can be processed and analysed to extract the meaningful information

A structured collection of data organized for easy access, mangaement and retrieval.
+ Stores information
+ Organizes Datas
+ Easy retrieval
+ Ensures consistency  
 It serves as a centralized repository, allowing data to be accessed, managed, and updated by multiple users or applications.
 
 Databases are essential because they:

- ****Scale efficiently**** to handle massive volumes of data.
- ****Ensure data integrity**** through built-in rules and constraints.
- ****Protect data**** with secure access controls and compliance support.
- ****Enable analytics**** by identifying trends and guiding informed business decisions.
  
**Working of Database**
Databases work by organizing and storing information in a structured or unstructured format, allowing easy access, retrieval, and modification. At the core of every database system is the ****Database Management System (DBMS)****—a software layer that acts as an intermediary between users and the raw data.

- The DBMS handles tasks like querying, updating, deleting and managing access permissions, without requiring users to know the physical details of where data is stored.
- When a user submits a request (such as a search or update), the DBMS processes the query, locates the relevant data, and returns results in a structured format.
- DBMSs provide features like backup, recovery, performance optimization and data security to ensure the system runs efficiently and reliably.
  
  **Types of Database**
  
  ****1. Relational Databases (RDBMS)****

Relational databases organize data into tables made up of rows (records) and columns (fields). They use schemas (blueprints) to define how data is structured and how different tables relate to each other.

- Strict schema-based structure.
- Primary Keys (unique IDs) and Foreign Keys (relationships between tables).
- Strong ACID compliance (Atomicity, Consistency, Isolation, Durability).
- Ideal for structured data.
  
  ****2. NoSql Databases ****

"NoSQL" stands for "Not Only SQL". These databases are designed to handle unstructured or semi-structured data, such as text, images, videos or sensor data. They don’t rely on the traditional table format.

- Flexible data models (no fixed schema).
- Scales horizontally for high-volume data.
- Often optimized for specific use cases like graphs or time-series data.
###### ACID Properties
ACID stands for Atomicity, Consistency, Isolation, and Durability—four essential principles that ensure your database transactions are reliable, accurate, and secure.

- **Atomicity**: Ensures transactions complete fully or not at all.
- **Consistency**: Ensures the database moves from one valid state to another.
- **Isolation**: Ensures that multiple transactions can happen at the same time without affecting each other.
- **Durability**: Saves changes permanently after completion.
  
###### **SQL SKILLS**
 To excel in SQL-related roles, mastering the following skills is essential:

- ****Querying****: Writing efficient SELECT, JOIN, and subquery statements.
- ****Database Design****: Creating normalized tables, indexes, and constraints.
- ****Data Manipulation****: Using INSERT, UPDATE, DELETE, and transactions.
- ****Performance Optimization****: Analyzing query plans and optimizing with indexes.
- ****Integration****: Connecting SQL with tools like Python, Java, or testing frameworks.
- ****Security****: Preventing SQL injection and managing user permissions.

#### What is SQL?
Structured Query Language (SQL) is the standard language used to interact with the relational databases

| Before SQL           | After SQL      |
| -------------------- | -------------- |
| Manual file system   | Structred Data |
| Slow retrieval       | Fast querying  |
| Inconsistent storage | Data integrity |
|                      |                |
## Key Components of a SQL System

- **Databases** : A database is a structured collection of data. It organizes data into ***tables****, which are like spreadsheets with rows (records) and columns (fields) .
- **Tables**: Each table enforces rules and relationships among its columns for data integrity.
- **Indexes**: Indexes speed up queries by allowing the database to quickly locate data without scanning the entire table.
- **Views****: A view is a virtual table basically a saved SELECT statement you can query like a table.
- **Stored Procedures**: These are pre-written SQL scripts stored inside the database. They can receive inputs, run complex logic and return results boosting performance, reusability and security.
- **Transactions**: A transaction groups multiple SQL operations into a single unit. It ensures ***all** changes are applied successfully or none are, preserving data integrity (ACID properties)
- **Security and Permissions**: SQL includes tools to ***restrict access**, letting DBAs assign who can do what whether it's accessing tables, executing procedures, or changing structures.
- **Joins:** Joins combine data from multiple tables based on relationships essential for querying across related datasets.

## Rules for Writing SQL Queries

There are certain rules for SQL which would ensure consistency and functionality across databases. By following these rules, queries will be well formed and well executed in any database.

- **End with Semicolon (******`;`******)****: Each SQL statement must end with a semicolon to execute properly.
- **Case Insensitivity****: SQL keywords (e.g., SELECT, INSERT) are not case-sensitive. However, table or column names may be case-sensitive depending on the DBMS.
- **Whitespace Allowed****: Queries can span multiple lines, but use spaces between keywords and names.
- **Reserved Words****: Avoid using SQL keywords as names. If needed, wrap them in quotes (`" "`) or backticks (`).

****Comments****

- Single-line: -- comment
- Multi-line: /* comment */

**Data Constraints****: Use NOT NULL, UNIQUE, PRIMARY KEY, etc., to ensure data accuracy.

**String Values****: Enclose strings in single quotes ('text').

**Naming Rules:****

- We Start with a letter
- We can only use Max 30 characters
- We only use letters, numbers and underscores (_)

## What are Different SQL Commands or Queries?

Structured Query Language (SQL) commands are standardized instructions used by developers to interact with data stored in ****relational databases****. These commands allow for the creation, manipulation, retrieval and control of data, as well as database structures. SQL commands are categorized based on their specific functionalities:![[Pasted image 20251218150424.png]]

### 1. Data Definition Language

These commands are used to define the structure of database objects by ****creating****, ****altering**** and ****dropping**** the database objects. Based on the needs of the business, database engineers create and modify database objects using DDL. The [CREATE](https://www.geeksforgeeks.org/sql/sql-create-table/) command, for instance, is used by the database engineer to create database objects like tables, views and indexes.

|Command|Description|
|---|---|
|CREATE|Creates a new table, a view on a table, or some other object in the database.|
|ALTER|Modifies an existing database object, such as a table|
|DROP|Deletes an entire table, a view of a table, or other objects in the database|
|TRUNCATE|Removes all records from a table but keeps the table structure intact.|
|RENAME|It is used to change the name of an existing database object, such as a table.|

### 2. Data Manipulation Language 

A relational database can be updated with new data using data manipulation language ([DML](https://www.geeksforgeeks.org/dbms/dml-full-form/)) statements. The INSERT command, for instance, is used by an application to add a new record to the database.

|Command|Description|
|---|---|
|INSERT|Creates a record.|
|UPDATE|Modifies records.|
|DELETE|Deletes records.|

### 3. Data Query Language

Data retrieval instructions are written in the data query language ([DQL](https://www.geeksforgeeks.org/sql/dql-full-form/)), which is used to access relational databases. The [SELECT](https://www.geeksforgeeks.org/sql/sql-select-query/) command is used by software programs to filter and return particular results from a SQL table. 

### 4. Data Control language

DCL commands manage user access to the database by granting or revoking permissions. Database administrators use [DCL](https://www.geeksforgeeks.org/sql/dcl-full-form/) to enforce security and control access to database objects.

|Command|Description|
|---|---|
|GRANT|Gives a privilege to the user.|
|REVOKE|Takes back privileges granted by the user.|

### 5. Transaction Control Language

TCL commands manage transactions in relational databases, ensuring data integrity and consistency. These commands are used to commit changes or roll back operations in case of errors.

|Command|Description|
|---|---|
|COMMIT|Saves all changes made during the current transaction on a permanent basis. Some databases provide an auto-commit feature, which can be configured using settings.|
|ROLLBACK|Reverts changes made during the current transaction, ensuring no unwanted changes are saved.|
|SAVEPOINT|Sets a point within a transaction to which changes can be rolled back, allowing partial rollbacks|

#### **SQL Data Types**

6 types of data types:

1. Numeric data types.
	+ Numeric data types used to store numbers, whether they are integers, decimal or floating-point numbers.
	+ these data types allow for the mathematical operations like addition, subtraction, multiplication and division
	  
	**EXACT NUMERIC TYPE:**

| Datatype | Description                                            | Range                                                       |
| -------- | ------------------------------------------------------ | ----------------------------------------------------------- |
| BIGINT   | Large integer numbers                                  | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807     |
| INT      | Standard integer values                                | -2,147,483,648 to 2,147,483,647 or -2 billion to +2 billion |
| SMALLINT | Small integers                                         | -32,768 to 32,767                                           |
| TINYINT  | Very small integers                                    | 0 to 255                                                    |
| DECIMAL  | Exact fixed-point numbers (e.g., for financial values) | -10^38 + 1 to 10^38 - 1                                     |
| NUMERIC  | Similar to DECIMAL, used for precision data            | -10^38 + 1 to 10^38 - 1                                     |
		**APPROXIMATE NUMERIC TYPE:**

| Datatype | Description                               | Range                   |
| -------- | ----------------------------------------- | ----------------------- |
| FLOAT    | Approximate numeric values                | -1.79E+308 to 1.79E+308 |
| REAL     | Similar to FLOAT, but with less precision | -3.40E+38 to 3.40E+38   |

2. Character and string data types.
	+  Character data type is used to store text or character-based data.

| Datatype      | Description                                                                                                 |
| ------------- | ----------------------------------------------------------------------------------------------------------- |
| Char          | The maxi length of 8000 characters (fixed length non-unicode characters)                                    |
| Varchar       | The maxi length of 8000 characters (varaible length non-unicode characters)                                 |
| Varchar (max) | The maximum length of ****2^31 - 1**** characters(SQL Server 2005 only). (Variable Length non-Unicode data) |
| Text          | The maximum length of 2,127,483,647 characters(Variable Length non-Unicode data) 2 million                  |
Unicode Character string Data types
+ Unicode data types are used to store characters from any language , support a wider variety of characters

| Datatype       | Description                                                                                     |
| -------------- | ----------------------------------------------------------------------------------------------- |
| Nchar          | The maximum length of 4000 characters(Fixed-Length Unicode Characters)                          |
| Nvarchar       | The maximum length of 4000 characters.(Variable-Length Unicode Characters)                      |
| Nvarchar (max) | The maximum length of 2^31 - 1 characters(SQL Server 2005 only). (Variable Length Unicode data) |

2. Date and time data types
	 + Storing date and time information. Essential for managind timestample, event and time based queries.
	 + DATE - stores the data of date (year, month, day)   - 3 bytes
	 + TIME  - stores the data of time (hour, minute, second)   -  3 bytes
	 + DATETIME - Store both the data and time (year, month, day, hour, minute, second)   -  8 bytes
3. Binary data types
	+ used to store binary data such as images videos or other file types
	+ Binary  -  FIXED LENGTH BINARY DATA    -   8000 bytes
	+ VarBinary  -  Variable lenght binary data   -   8000 bytes
	+ Image     -   stores binary data as images   - 2,147,483,647 bytes
4. Boolean data types
	+ used to store logical values, typically true or false.It is commonly used for flag fields or binary conditions.
>> 	 CREATE TABLE User_Status (  
	    UserID INT PRIMARY KEY,  
	    IsActive BIT,  
	    IsVerified BIT  
		);
5. Special data type
	+ Sql support some specialized data types for advanced use cases
	+ XML Data type: 
		+ Used to store XML data and manipulate XML structure in the DB
		  Example:
			>>  CREATE TABLE XML_Records (  
			    RecordID INT PRIMARY KEY,  
			    ConfigData XML  
				);
	 + Spatial Data type:
		 + stores planar spatial data such as points, lines and polygons in a databasetable
		   Example
			>> CREATE TABLE Locations (  
			    LocationID INT PRIMARY KEY,  
			    Area GEOMETRY  
				 ); 

###### ***SQL CREATE TABLE***

To CREATE TABLE statement in sql is used to define a new table in a database.
It specifies **table name, column name and the data types**.

**SYNTAX**
CREATE table table_name
(
Column 1 datatype (size),
Column 2 datatype (size),
.
.
ColumnN datatype (size)
)

Table_name: the name you assign to the new tables
Column 1, column 2,..: the names of the columns in the table. 
Datatype (size): Defines the datatype and size of each column

Example:
CREATE TABLE customer{
CustomerID INT PRIMARY KEY,
CustomerName VARCHAR (50),
LastName VARCHAR (50),
AGE INT CHECK (Age>=0 AND Age<=99),
Phone INT CHECK(Phone=10)
}

**Table creation in MYSQL**
CREATE TABLE customer (
CustomerID TINYINT PRIMARY KEY,
CustomerName VARCHAR (50),
LastName VARCHAR (50),
AGE TINYINT CHECK (Age>=0 AND Age<=99),
Phone BIGINT UNSIGNED
)

INT depreceated in MySQL 8+
TINYINT - 0-255 so we use BIGINT