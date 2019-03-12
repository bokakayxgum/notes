# Part 1: Understanding Databases
## What are Databases?

1.  Size – Scalable 
2.	Ease of updating – Accessible 
3.	Accuracy – Accurate 
4.	Security – Secure 
5.	Redundancy – Consistent 
6.	Importance – Permanent 
Database give us structure.

## Exploring Databases and Database Management Systems?

1. Example DBMS : Oracle, SQL Server, My SQL, Postgre SQL, MongoDB

2. DBMS Software
   ![1](1.PNG)
* DBMS software like Oracle or DB2 not installed on personal machine but on a separate server.
* Use that DBMS software to create or manage one or more databases.
* Database is your data and your rules about that data.
* Company can have multiple databases or DBMS management systems.

3. Relational DBMS
* Are the most widely used 
* Use the same principal across all offerings.
* Are foundational for understanding other systems

# Part2: Database Fundamentals
## The feature of relational Database

![2](2.PNG)

* A table is most fundamental building block of a
  database

1. A database without table is an empty sheel, devoid of meaning

   ![3](3.PNG)

   A <b>key</b> is a  way to identify just one particular row in any table and it's created typically as one column that will contain a guaranteed unique value for each row. 

   ![4](4.png) 

   * Each column describes one piece of data
   * It also says what type of the data must be\
   * DBMS system will not let us break them
   * Tables and columns are defined up front
   * Day-to-day use is in creating and updating rows

   

## Unique Values and Primary Keys

* Each column describes one piece of data

* It also says what type of the data must be

* DBMS system will not let us break them

* Tables and columns are defined up front

* Day-to-day use is in creating and updating rows

![5](5.png)

## Defining Table Relationships

![7](7.PNG)



Example:

![8](8.PNG)

* Customer ID : automatically generate a unique number

![9](9.PNG)



Each order is an order for a particular customer, to process an order, you would need to know who this applies to.

![10](10.PNG)

We could to above. But, don't. Why

* Duplication of Data

* No need to do this

  

![11](11.PNG)'

* formal relationship between tables
* In order table, the customer ID does not have to be unique
* customer ID is foreign key

![12](12.PNG)

* start at customer row and then take that Customer ID and go get every order for that customer
* go from the order row and find Customer ID  and then find out which customer is associated with that particular order
* one-to-many relationship
* one customer can have many orders

![13](13.PNG)

* crow's foot symbol

* one-to-infinity symbol 

## Describing many-to-many relationships

* no obvious to spot

* you cannot express many-to-many relationships directly

Example:

![14](14.PNG)

* **Bad** Repeating Group or Repeating Column

![15](15.PNG)

* **Bad** Discourage as well

![16](16.PNG)

* not unique in the junction table 

One-to-one relationships is possible but why don't just combine them?

## Transaction and the ACID Test

![17](17.PNG)

**Transaction** is a combine unit of work 

* both of these happens or neither of them
* first part of the transaction failed if any part of the transactions failed

![18](18.PNG)

* **Atomic** : must have happened or not at all
* **Consistent** : Any transaction must take the database from one valid state to another valid state based on the rules of the database
* **Isolated**: No other transactions are allowed until the transaction have finished
* **Durable**: Robust eg. power failure shouldn't be an issue after your transaction is made

## Introduction to Structured Query Language (SQL)

**SQL** is used to describe what you want and you let the database management system handle how that's actually done. You just describe the outcome.

![20](20.PNG)

![21](21.PNG)

# Part3: Database Modeling: Tables

## Introduction to database modeling

* agile
* planning

## Planning your database 

![22](22.PNG)

![23](23.PNG)

![24](24.PNG)

* Identify what entities we naturally have

![25](25.PNG)

* In relational databases, we only concern about what data need to be saved.
* Entity modeling (ER modeling)

## Identifying Columns and selecting data types

* Specify what data is store in each entity. In entity relationship, these are referred to as our **attributes**

  ![26](26.PNG)

  

![27](27.PNG)

* go very granular, as individual as possible
* don't use space

![28](28.PNG)

* MySQL have different types of int (Go to dev.msql.com)

  ![29](29.PNG)

  

* Fixed Length (if more than the fixed length, extras character will be terminated)
* Unicode (For foreign language)

* Binary data

* Binary Large Objects (BLOBS)

* Character Large Objects (CLOBS)

  

![30](30.PNG)

* Sometimes you don't required a value

* NULL is complete absence of a value

* not NULL, a value is required

  

![31](31.PNG)

## Choosing Primary Keys

* Each table should have primary keys, a value that uniquely identifies an individual where there can be no duplicated and no confusion

* Natural Key (e.g. ISBN)

  

![32](32.PNG)

* Add a CustomerID column and then make it automatically increment

## Using composite keys

* **Composite Key** is when one value does not uniquely identify a row, but two values do, we'd combine tow columns values to create unique primary key

* Useful when joining tables together (many-to-many relationships)

![33](33.PNG)

# Part4: Database Modeling Relationships

## Creating relationships

![34](34.PNG)

We need to say what these relationships are.

## Defining One-to-Many Relationships

![35](35.PNG)

![36](36.PNG)

![37](37.PNG)

![38](38.PNG)

* Refer to one and only one row in the customer table
* One customer can have many orders, but one order cannot have many customers

![39](39.PNG)

* In some cases, we can't use the same name for Foreign Key because there will be a conflict

![40](40.PNG)

![41](41.PNG)

![42](42.PNG)

## Exploring One-to-One Relationships

![43](43.PNG)

![44](44.PNG)

* Might as well just combine them

![45](45.PNG)

* always look at relationship on both ways when you thought you have found both way

## Exploring many-to-many relationships

![47](47.PNG)

![48](48.PNG)

* We don't need primary key for ClassStudent

## Understanding Relationships Rules and Referential Integrity

![49](49.PNG)

* Add a new order with a customer ID 388 but there's no customer ID 388
* The database is no longer valid, it would not be internally consistent. **Referential Constraint**
* Must add customer first!!!

![50](50.PNG)

![51](51.PNG)

* Updates will not work as well

![52](52.PNG)

* Any associate row will be deleted. Delete 367 will delete Order 101 and 102

  

![53](53.PNG)

![54](54.PNG)

* refuse the delete

# Part5: Database Modeling Optimization

## Understanding Normailization

* Database Normalization

## First Normal Form

Each of your columns and each of your tables should contain one value, just one value and there should be no repeating groups.

![55](55.PNG)

![55](55.PNG)

![56](56.PNG)

Violates First Normal Form

![57](57.PNG)

* inflexible design

![58](58.PNG)

## Second Normal Form

* Any non-key field ( the actual value in a particular column position for a particular row) should be dependent on the entire primary key

* **2NF is only a problem when we are using a composite primary key** (a primary key made of 2 or more columns) 
* Can I figure out any values in this row from just part of the composite key? No

![59](59.PNG)

![60](60.PNG)

What if someone only changes the Course but not the Course Title?

![61](61.PNG)

##  Third Normal Form

* No non-key field is dependent on any other non-key field

* Can I figure put any of the values in this row, from any of the other values in this row? Should not be able to do that!

  

![62](62.PNG)

* each room has a fixed number of seats

  ![63](63.PNG)

![64](64.PNG)

* Total is dependent on the other two non-key fields
* Remove the **Total** column, we will figure it out

![65](65.PNG)

![66](66.PNG)

## Database Normalization

![67](67.PNG)

It can be easier to add repeating group rather than adding multiple tables. **Denormalization Decision**

![68](68.PNG)

Some zip codes may have multiple city, town or even states!

![69](69.PNG)

# Part6: Database Modeling (Querying)

## Creating SQL Queries

![70](70.PNG)

![71](71.PNG)

![72](72.PNG)

![73](73.PNG)

![74](74.PNG)

![75](75.PNG)

SQL does not care if Select is Uppercase or Lowercase

SQL not sensitive to line breaks, white space

![76](76.PNG)

How to know which table?

![77](77.PNG)

Making assumptions that we have a database called Human Resources

## Structuring the WHERE clause

* WHERE part that specifying a condition or predicate

  

![78](78.PNG)

![79](79.PNG)

![80](80.PNG)

Just single = 

![81](81.PNG) no need to quote if it is just value

![82](82.PNG)

![83](83.PNG)

![84](84.PNG)

![85](85.PNG)

wild card! 

![86](86.PNG)

Using likes can be inefficient!

![87](87.PNG)

Not a good choice to use = sign 



![88](88.PNG)

IS NULL

![89](89.PNG)

IS NOT NULL

## Sorting Query Results

![90](90.PNG)

Not finding this useful e.g. Find out the most expensive product that I have

By default, order is in **ascending order**

![91](91.PNG)

![92](92.PNG)

## Using Aggregate Functions

![93](93.PNG)COUNT

MAX

MIN

SUM



![94](94.PNG)

![95](95.PNG)

It can either give you the single count of all rows, or it can give you all the multiple values in the color column



![96](96.PNG)

## Joining Tables

* To join our tables together



![97](97.PNG)

* Alice does not have a match --> Inner Join 
* JOIN is default to INNER JOIN

![98](98.PNG)

* OUTER JOIN --> something take precedance

![99](99.PNG)

![100](100.PNG)

## Inserting, updating, and deleting



![101](101.PNG)

![102](102.PNG)

![103](103.PNG)

![104](104.PNG)

## The data definition languages



![105](105.PNG)

![106](106.PNG)

![107](107.PNG)

People will use **MySQL Workbench** or **SQL Server Management Studio**

# Part7: Database Modeling: Indexing and Optimization

## Understanding indexes

* An index in the database is like an index in a textbook
* Primary key does not answer if it can help us to find the row really fast
* Primary index on any table is called **Clustered Index**
* Most of the DBMS will automatically make the primary key the clustered index
* Each table can only have one clustered index

![108](108.PNG)

Full Table Scan very inefficient way to get to your data



![109](109.PNG)



![110](110.PNG)

## Understanding write conflicts

![111](111.png)

Race Condition



![112](112.png)

dirty read

![113](113.png)

![114](114.png)

## Understanding stored procedures and injection attacks

Stored Procedures/ SProc

![ 115](115.png)

![116](116.png)

![117](117.png)

![118](118.png)

![119](119.png)

Use Stored Procedures with  parameter rather then constructing your own strings



# Part8: Database Options

## Desktop databases

* Microsoft Access, FileMaker Pro Advanced, Apache OpenOffice

![120](120.png)

![121](121.png)

## Relational databases management

* Mircrosoft Azure and Amazon Web Service you can pay them and then you build the infrastructure
* Express edition is free (DB2 Express-C, SQL Server Expres)

## XML and Object-Oriented Databases

![122](122.png)

* XML documents use the nested tree structure of XML 
* Use XML languages (Xquery) to query data rather than using SQL

![123](123.png)

![124](124.png)

* User ORM to map objects in an object-oriented language to regular relational database tables

## NoSQL Database Systems (Not only SQL)



![125](125.png)

* Skills in each db is not transferable

![126](126.png)

![127](127.png)

![128](128.png)

![129](129.png)

![130](130.png)

![131](131.PNG)