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

   ![4](4.PNG) 

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

![5](5.PNG)

## Defining Table Relationships

![7](7.PNG)



Example:

![8](8.png)

* Customer ID : automatically generate a unique number

![9](9.png)



Each order is an order for a particular customer, to process an order, you would need to know who this applies to.

![10](10.png)

We could to above. But, don't. Why

* Duplication of Data

* No need to do this

  

![11](11.png)'

* formal relationship between tables
* In order table, the customer ID does not have to be unique
* customer ID is foreign key

![12](12.png)

* start at customer row and then take that Customer ID and go get every order for that customer
* go from the order row and find Customer ID  and then find out which customer is associated with that particular order
* one-to-many relationship
* one customer can have many orders

![13](13.png)

* crow's foot symbol

* one-to-infinity symbol 

## Describing many-to-many relationships

* no obvious to spot

* you cannot express many-to-many relationships directly

Example:

![14](14.png)

* **Bad** Repeating Group or Repeating Column

![15](15.png)

* **Bad** Discourage as well

![16](16.png)

* not unique in the junction table 

One-to-one relationships is possible but why don't just combine them?

## Transaction and the ACID Test

![17](17.png)

**Transaction** is a combine unit of work 

* both of these happens or neither of them
* first part of the transaction failed if any part of the transactions failed

![18](18.png)

* **Atomic** : must have happened or not at all
* **Consistent** : Any transaction must take the database from one valid state to another valid state based on the rules of the database
* **Isolated**: No other transactions are allowed until the transaction have finished
* **Durable**: Robust eg. power failure shouldn't be an issue after your transaction is made

## Introduction to Structured Query Language (SQL)

**SQL** is used to describe what you want and you let the database management system handle how that's actually done. You just describe the outcome.

![20](20.png)

![21](21.png)

# Part3: Database Modeling: Tables

## Introduction to database modeling

* agile
* planning

## Planning your database 

![22](22.png)

![23](23.png)

![24](24.png)

* Identify what entities we naturally have

![25](25.png)

* In relational databases, we only concern about what data need to be saved.
* Entity modeling (ER modeling)

## Identifying Columns and selecting data types

* Specify what data is store in each entity. In entity relationship, these are referred to as our **attributes**

  ![26](26.png)

  

![27](27.png)

* go very granular, as individual as possible
* don't use space

![28](28.png)

* MySQL have different types of int (Go to dev.msql.com)

  ![29](29.png)

  

* Fixed Length (if more than the fixed length, extras character will be terminated)
* Unicode (For foreign language)

* Binary data

* Binary Large Objects (BLOBS)

* Character Large Objects (CLOBS)

  

![30](30.PNG)

* Sometimes you don't required a value

* NULL is complete absence of a value

* not NULL, a value is required

  

![31](31.png)

## Choosing Primary Keys

* Each table should have primary keys, a value that uniquely identifies an individual where there can be no duplicated and no confusion

* Natural Key (e.g. ISBN)

  

![32](32.PNG)

* Add a CustomerID column and then make it automatically increment

## Using composite keys

* **Composite Key** is when one value does not uniquely identify a row, but two values do, we'd combine tow columns values to create unique primary key

* Useful when joining tables together (many-to-many relationships)

![33](33.png)

# Part4: Database Modeling Relationships

## Creating relationships

![34](34.png)

We need to say what these relationships are.

## Defining One-to-Many Relationships

![35](35.png)

![36](36.png)

![37](37.png)

![38](38.png)

* Refer to one and only one row in the customer table
* One customer can have many orders, but one order cannot have many customers

![39](39.png)

* In some cases, we can't use the same name for Foreign Key because there will be a conflict

![40](40.png)

![41](41.png)

![42](42.png)

## Exploring One-to-One Relationships

![43](43.png)

![44](44.png)

* Might as well just combine them

![45](45.png)

* always look at relationship on both ways when you thought you have found both way

## Exploring many-to-many relationships

![47](47.png)

![48](48.png)

* We don't need primary key for ClassStudent

## Understanding Relationships Rules and Referential Integrity

![49](49.png)

* Add a new order with a customer ID 388 but there's no customer ID 388
* The database is no longer valid, it would not be internally consistent. **Referential Constraint**
* Must add customer first!!!

![50](50.png)

![51](51.png)

* Updates will not work as well

![52](52.png)

* Any associate row will be deleted. Delete 367 will delete Order 101 and 102

  

![53](53.png)

![54](54.png)

* refuse the delete

# Part5: Database Modeling Optimization

## Understanding Normailization

* Database Normalization

## First Normal Form

Each of your columns and each of your tables should contain one value, just one value and there should be no repeating groups.

![55](55.png)

![55](55.png)

![56](56.png)

Violates First Normal Form

![57](57.png)

* inflexible design

![58](58.png)

## Second Normal Form

* Any non-key field ( the actual value in a particular column position for a particular row) should be dependent on the entire primary key

* **2NF is only a problem when we are using a composite primary key** (a primary key made of 2 or more columns) 
* Can I figure out any values in this row from just part of the composite key? No

![59](59.png)

![60](60.png)

What if someone only changes the Course but not the Course Title?

![61](61.png)

##  Third Normal Form

* No non-key field is dependent on any other non-key field

* Can I figure put any of the values in this row, from any of the other values in this row? Should not be able to do that!

  

![62](62.png)

* each room has a fixed number of seats

  ![63](63.png)

![64](64.png)

* Total is dependent on the other two non-key fields
* Remove the **Total** column, we will figure it out

![65](65.png)

![66](66.png)

## Database Normalization

![67](67.png)

It can be easier to add repeating group rather than adding multiple tables. **Denormalization Decision**

![68](68.png)

Some zip codes may have multiple city, town or even states!

![69](69.png)

# Part6: Database Modeling (Querying)

## Creating SQL Queries

![70](70.png)

![71](71.png)

![72](72.png)

![73](73.png)

![74](74.png)

![75](75.png)

SQL does not care if Select is Uppercase or Lowercase

SQL not sensitive to line breaks, white space

![76](76.png)

How to know which table?

![77](77.png)

Making assumptions that we have a database called Human Resources

## Structuring the WHERE clause

* WHERE part that specifying a condition or predicate

  

![78](78.png)

![79](79.png)

![80](80.png)

Just single = 

![81](81.png) no need to quote if it is just value

![82](82.png)

![83](83.png)

![84](84.png)

![85](85.png)

wild card! 

![86](86.png)

Using likes can be inefficient!

![87](87.png)

Not a good choice to use = sign 



![88](88.png)

IS NULL

![89](89.png)

IS NOT NULL

## Sorting Query Results

![90](90.png)

Not finding this useful e.g. Find out the most expensive product that I have

By default, order is in **ascending order**

![91](91.png)

![92](92.png)

## Use Aggregate Functions



![93](93.png)

![94](94.png)

![95](95.png)

![96](96.png)

![97](97.png)

![98](98.png)

![99](99.png)

![100](100.png)

![101](101.png)

![102](102.png)

![103](103.png)

![104](104.png)

![105](105.png)

![106](106.png)

![107](107.png)

![108](108.png)

![109](109.png)

![110](1110.png)