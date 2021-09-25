# nosql vs sql
|SQL                                   |NoSQL                                          |
|:-----------                          |--------------:                                | 
|     databases are primarily called as Relational Databases (RDBMS)                                 |  database are primarily called as non-relational or distributed database.                                             |
|databases have predefined schema whereas                                 |                                 databases have dynamic schema for unstructured data.              |
|databases are vertically scalable whereas the                               |                  databases are horizontally scalable                              |
|     databases uses SQL ( structured query language ) for defining and manipulating the data, which is very powerful                                  |                   database, queries are focused on collection of documents.                             |

### 1.What kind of data is a good fit for an SQL database?
SQL databases are good fit for the complex query intensive environment 
### 2.Give a real world example.
1. MySQL Community Edition
MySQL database is very popular open-source database. It is generally been stacked with apache and PHP, although it can be also stacked with nginx and server side javascripting using Node js

### 3.What kind of data is a good fit a NoSQL database?
NoSQL databases are not good fit for complex queries. On a high-level, NoSQL don’t have standard interfaces to perform complex queries, and the queries themselves in NoSQL are not as powerful as SQL query language.
NoSQL database fits better for the hierarchical data storage as it follows the key-value pair way of storing data similar to JSON data. NoSQL database are highly preferred for large data set (i.e for big data). Hbase is an example for this purpose.
### 4.Give a real world example.
1. MongoDB
Mongodb is one of the most popular document based NoSQL database as it stores data in JSON like documents. It is non-relational database with dynamic schema. It has been developed by the founders of DoubleClick, written in C++ and is currently being used by some big companies like The New York Times, Craigslist, MTV Networks. The following are some of MongoDB benefits and strengths:



### 5.Which type of database is best for hierarchical data storage?
NoSQL database fits better for the hierarchical data storage as it follows the key-value pair way of storing data similar to JSON data. NoSQL database are highly preferred for large data set (i.e for big data). Hbase is an example for this purpose.
### 6.Which type of database is best for scalability?
 In most typical situations, SQL databases are vertically scalable. You can manage increasing load by increasing the CPU, RAM, SSD, etc, on a single server. On the other hand,



 ===============================================================================================
 # sql vs nosql 
### 1.What does SQL stand for? 

Structured Query Language
### 2.What is a realational database?
database which works with certain assumptions or in certain way 
### 3.What type of structure does a relational database work with?
table is like a data bin astorage container
### 4.What is a ‘schema’?
schema is defined by so-called fields
### 5.What is a NoSQL database?
simply stemming from the word gumongous because its built to store lots and lots of datain very efficient way
### 6.Howo does it work?
NoSQL is an approach to databases that represents a shift away from traditional relational database management systems (RDBMS). ... Relational databases rely on tables, columns, rows, or schemas to organize and retrieve data. In contrast, NoSQL databases do not rely on these structures and use more flexible data models.
### 7.What is inside of a Mongo database?
collections in such a collection we have so-called documents  
### 8.Which is more flexible - SQL or MongoDB? and why.
MongoDB is more flexible you can add new data. there is no schema implied and thir no realational
### 9.What is the disadvantage of a NoSQL database?
it have some duplicates data 