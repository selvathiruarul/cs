# Database Design and Management

A **database** is an *organized collection of data* (help people keep trak of thinks). It is the collection of schemes, tables, queries, reports, views and other objects.

A **database management system** (DBMS) is a computer software application that interacts with the user, other applications, and the database itself to capture and analyze data. A general-purpose DBMS is designed to allow the definition, creation, querying, update, and administration of databases. Well-known DBMSs includes: [MySQL](https://www.mysql.com/), [PostgreSQL](http://www.postgresql.org/), [Microsoft SQL Server](http://www.microsoft.com/en-us/server-cloud/products/sql-server/features.aspx), [Oracle](https://www.oracle.com/database/index.html), [Sybase](www.sap.com/Database) and [IBM DB2](http://www-01.ibm.com/software/data/db2/).

- [Glossary](https://github.com/valerysamovich/engineering/blob/master/docs/tutorials/database.md#glossary)

## Context

- Database Fundamentals
  - [Introduction](/docs/tutorials/database.md#introduction)
    - [Database History](/docs/databases/database-design-managment.md#history-of-databases)
    - [Data volume](/docs/databases/database-design-managment.md#data-volume)
  - [Relational Model](https://github.com/valerysamovich/engineering/blob/master/docs/tutorials/database.md#the-relational-model)
  - [Structured Query Language](https://github.com/valerysamovich/engineering/blob/master/docs/tutorials/database.md#structured-query-language) (SQL)
- Database Design 
  - [Data Modeleing and Entity Relationship Diagram](https://github.com/valerysamovich/engineering/blob/master/docs/tutorials/database.md#data-modeling-and-ert) (ERD)
  - [Database Design](https://github.com/valerysamovich/engineering/blob/master/docs/tutorials/database.md#database-design)
- Database Management
  - [Database Administration](https://github.com/valerysamovich/engineering/blob/master/docs/tutorials/database.md#database-administration)
  - [Big Data, Data Warehouses, and Business Intelligence Systems](https://github.com/valerysamovich/engineering/blob/master/docs/tutorials/database.md#big-data-data-warehouses-and-business-intelligence-systems)

## Introduction

The **first** patent for a **data storage device** was issued to *Herman Hollerith in 1884 for his punched card*. Hollerith worked in the Census Office of the U.S. government. The census in the U.S. is conducted every ten years to count the population. The census of 1880 took eight years.

The importance of database processing increases every day because databases are used in information systems everywhere—and increasingly so. The **purpose of a database** is to help people keep track of things. Lists can be used for this purpose, but if a list involves more than one theme modification problems will occur when data are inserted, updated, or deleted.

**Relational databases** store data in the form of tables. Almost always, the tables are designed so that each table stores data about a single theme. Lists that involve multiple themes need to be broken up and stored in multiple tables, one for each theme. When this is done, a column needs to be added to link the tables to each other so that the relationship from a row in one table to a row in another table can be shown.

A **modification problem** is a data corruption or loss that occurs when a table uses one row to store facts about two or more themes. In this case, a deletion of a row can remove facts about two or more themes, leading to a loss in data, or a data change must be made in multiple rows to maintain data consistency. Finally, unless creation of a new row is allowed based on only one theme, it may be impossible to store needed data. 

An **anomaly** is defined as a abnormality or deviation from the expected. In a file system, an anomaly usually occurs when two or more files are merged to achieve data integration. Three possible modification **problems/anomalies** are:

- Insert problems — missing data
  - Insertion anomalies occur when adding data to a file that has redundancies.
- Update problems — inconsistent data
  - An update anomaly occurs when you make changes to records. 
- Delete problems — data loss.
  - Deletion anomalies occur when deleting a record from a file.

[**Structured Query Language**](https://github.com/valerysamovich/engineering/blob/master/docs/tutorials/database.md#structured-query-language) (SQL) is an international language for processing tables in relational databases. You can use SQL to join together and *display data stored in separate tables*, *create new tables*, and *query data from tables* in many ways. You can also use **SQL** to *insert*, *update*, and *delete* data.

The components of a **database system** are:

- Database
- Database management system (DBMS)
- Database applications (one or more)
- Users

A **database** is a *self-describing collection of related records*. A relational database is a self-describing collection of related tables. A database is self-describing because it contains a description of its contents within itself, which is known as metadata. Tables are related by storing linking values of a common column. The contents of a database are:

- User data
- Metadata (structure of the data)
  - names of tables
  - columns
  - indexes (used to improve database performance)
- Supporting structures (such as indexes)
- Application metadata (data that describe application elements)
  - Reports
  - Forms

A **database management system (DBMS)** is a large, complicated program used (or purpose) to create, process, and administer a database. DBMS products are almost always licensed from software vendors. Specific *functions* of a DBMS are summarized below:

- Create database
- Create tables
- Create supporting structures (e.g., indexes)
- Read database data
- Modify(insert, update, or delete) database data
- Maintain database structures
- Enforce rules
- Control concurrency
- Provide security
- Perform backup and recovery

The functions of **database applications** are:

- Create and process forms 
- Process user queries 
- Create and process reports
- Execute specific application logic
- Control the application. 

Users provide data and data changes and read data in forms, queries, and reports.

The term **referential integrity constraint** is a rule that before a possible key value of one table can be placed in a second table as a linking value, the value must exist in the first table before it is used in the second table.

DBMS products for **personal database systems** (Microsoft Access 2013 )provide functionality for application development and database management. They hide considerable complexity, but at a cost: Requirements unanticipated by DBMS features cannot be readily implemented. 

**Enterprise-class database systems** (Microsoft SQL Server 2014, Oracle MySQL 5.6, Oracle Database Express Edition 11 Release 2) include multiple applications that might be written in multiple languages. These systems may support hundreds or thousands of users.

**Data integration** is the ability to access all the pertinent data about an entity wherever that data may exist. Consider an employee file that contains a list of all current employees with their demographic and payroll information.

**Data redundancy** is the process of storing the same data more than once. Data integration can be quite high in a file based system but this often requires a high degree of data redundancy. Simply put, data integration is desirable but data redundancy is not.

## History of Databases

The first electronic storage of data was done in file systems. Previously we saw some of the problems that eventually developed. Due to growth in the amount of data stored and the increase in number of people needing access to that data, specialized software systems were developed to address data storage. This specialized software was called a database management system (DBMS). Historically, DBMSs have been categorized based on the data storage model used. There are five primary models:

- hierarchical models,
- network models,
- relational models,
- object-oriented models,
- NoSQL models.

**Hierarchical Models** Data in a hierarchical database is stored in a hierarchy or tree-like model. Actually it is better visualized as an upside down tree. The data radiates out from a common "root node" as shown in the figure. This root is the parent of all other nodes. A node can have any number of child nodes but each child node has only one parent node.

We can model student data using a hierarchical structure. Assume a student takes courses. Each student can take one or more courses. The best known hierarchical database was created by IBM in the mid 1960s for the Apollo moon missions. It was named Information Management System or IMS. This database is still available today.

The primary problem with the hierarchical data model is the complexity involved when making changes either to the database or the application software that uses the database.

**Network Models** Charles Bachman is generally credited with creating the network model of data storage. This model is similar to the hierarchical model except the network model allows multiple parent nodes for a child node instead of a single parent node. The model was standardized in 1969. Network databases were able to model the "real world" more closely than hierarchical databases. However they never gained wide spread acceptance for two reasons. First, IBM - the dominant technology company at the time - never adopted the network model choosing instead to add some network model features to its hierarchical database. The second reason was the development of the relational database.

**Relational Models** These types of databases are the focus of this course and will be covered in detail.

**Object-Oriented Models** Object-oriented databases have not achieved the level of success or market share in the business world that relational databases have enjoyed. This is primarily due to two factors. First, there is no standard language with which to add, manipulate, and retrieve data for these products. The Structured Query Language (SQL) exists for these purposes with respect to relational databases but no equivalent to SQL exists for object-oriented databases. Second, most of the major relational database vendors (Oracle, IBM, Microsoft) have been adding object-oriented features to their relational database product.

Object-oriented databases grew from the use of object-oriented programming languages like SmallTalk, C++, and Java. These languages create and manipulate electronic models of real world objects and it became necessary to store and manage these objects just like non object-oriented data.

The Object Query Language (OQL) is the latest attempt by a standards group (Object Data Management Group - ODMG) to create a common query language for object-oriented databases. The effort started in 1991 and the third revision of the standard was published in 2000. The ODMG was dissolved in 2001. To date you will still find a wide variety of "standards" in use with respect to object-oriented databases.

The primary advantages of OO databases compared to relational databases are:

- Data access will be faster compared to a relational database in many situations due to the way associated data is stored.
- OO databases more closely match the storage model used by OO programming languages.
- OO databases are made to store more complex types like audio, video, and web data.

**NoSQL Models** NoSQL databases were first developed in the late 1990s. These databases are not built using the relational model. NoSQL databases were developed in response to the difficulty of scaling up relational databases. Companies such as Google, Facebook, eBay, and Amazon store extremely large amounts of data. This data is often unstructured and doesn't exhibit relationships common in relational databases. Relational databases generally scale "up" by using larger, more powerful (and more expensive) servers. NoSQL databases scale "out" by using more servers and these servers are usually low cost inexpensive machines.

There are different interpretations of the explicit meaning of NoSQL is. One interpretation is literally that the database doesn't use the Structured Query Language (SQL). This is true for all the products in this category. Another interpretation is that NoSQL stands for "not only SQL" indicating a business may need a different type of database for large data storage. A relational database would still be used where appropriate.

NoSQL databases fall into several categories based on how they store data. These categories are document stores, key-value stores, column family stores, and graph databases. It is not important to know the details of each type for this course. It is only important to know there are different types of NoSql databases and the type depends on how the data is stored.

Specific products in this category include:

- Dynamo - a key-value NoSQL database created by Amazon.com
- Cassandra - a column oriented NoSQL database created by Facebook (and subsequently open-sourced)
- BigTable - column oriented NoSQL database created by Google
- CouchDB and MongoDB - document oriented NoSQL databases that are are open source.

## Data volume

The increasing volume of data and the expanding number of people requiring access to that data has led to additional issues including:

- data security
- data privacy
- data accuracy
- performance (fast access to data)
- data recovery.

**Data security** ensures that only authorized people access data. Certainly this involves limiting access via usernames and passwords and software security to prevent hacking. It also includes physical security. It is common to see a room with large computers protected with swipe card access but what about the personal computer on an employee's desk? The employee could have downloaded confidential data to this computer. Is this data secure?

**Data privacy** is ensuring an employee accesses the minimum amount of data necessary to complete his/her job. While I, as a Seminole State College employee, can access my salary data, I can't access the salary data of any other employee. Some staff members in the college Human Resources department can access salary data but not all department employees can.

**Data accuracy** involves the correctness and consistency of data. The volumes of data and multiple sources makes it more difficult to insure the data is correct. New files or databases are often created for new systems instead of using existing ones. This leads to the same data being stored in multiple places. It is not uncommon for people to receive multiple mailings from the same company. If a persons name is Robert, he might receive some mailings addressed to Robert and others addressed to Bob.

**Performance** becomes an issue when dealing with large amounts of data and an increasing number of people trying to access it. Fast computers and large network bandwidth can certainly help. However the fastest computers and the speediest networks can't overcome a poorly designed database that stores large amount of data. Even a well designed database will have performance issues if it isn't tuned properly.

**Recovery** capabilities are necessary to ensure data can be reconstructed if it is stolen, lost, or corrupted. Data can be damaged or destroyed by hardware failures, software errors, or even natural disasters like floods, hurricanes, and earthquakes. How long would employees patiently wait if the computer used to create their paychecks was destroyed along with the payroll data? I suspect it would be days not weeks! Imagine if the online site for a major airline crashed and was unavailable for several hours. The airline could lose millions of dollars as potential customers could easily switch to another airline's site. Healthcare in America is moving towards a paperless environment with electronic medical records, computerized admissions, automated pharmacy and prescription operations as well as a variety of other efforts. Imagine what would happen if the data to support all these areas wasn't available!

## The Relational Model

The **relational model** is the most important standard in database processing today. It was first published by **E. F. Codd** in 1970. Today, it is used for the *design and implementation of almost every commercial database*.

An **entity** is the formal name for a “thing” that is being tracked in a database, and is something of importance to a user that needs to be represented in a database. A **relation** is a two-dimensional table that has the characteristics listed below:

- Rows contain data about entity.
- Columns contain data about attributes of the entity.
- Cells of the table holds a single value.
- All entries in a column are of the same kind.
- Each column has a unique name.
- The order of the column is unimportant.
- The order of the rows is unimportant.
- No two rows may hold identical sets of data values.

Example of the **relation structure**:

    TABLE_NAME(Column1, Column2, Column3...., LastColumn)

Relation structures, such as one above, are part of a database schema. A **database schema** is a design on which a database and its associated applications are build.

In the database world in general, the term **table** is used synonymously with the term **relation**. Three sets of terminology are used for relational structures. Sometimes these terms are mixed and matched. Strictly speaking, a *relation may not have duplicate rows*; however, sometimes this condition is relaxed because eliminating duplicates can be a time-consuming process:

Table    | Row    | Column
---------|--------|----------
File     | Record | Field
Relation | Tuple  | Attribute

A **key** is one or more columns of a relation that is used to identify a row. A **unique key** identifies a single row; a **nonunique key** identifies several rows. A **composite key** is a key that has two or more attributes. A relation has one primary key, which must be a unique key. A relation may also have additional unique keys, called **candidate keys**. A primary key is used to represent the table in relationships, and many DBMS products use values of the primary key to organize table storage. In addition, an index normally is constructed to provide fast access via primary key values. An **ideal primary key** is short, numeric, and never changes.

A **surrogate key* is a unique numeric value that is appended to a relation to serve as the primary key. Surrogate key values have no meaning to the user and are normally hidden on forms, query results, and reports. They values supplied automatically by the DBMS.

A **foreign key** is an attribute that is placed in a relation to represent a relationship. A foreign key is the primary key of a table that is different from (foreign to) the table in which it is placed. Primary and foreign keys may have different names, but they must use the same data types and sets of values. A **referential integrity constraint** specifies that the values of a foreign key be present in the primary key.

A **primary key** is one or more attributes that functionally determines all of the other attributes. A primary key can be used:

- to identify a row.
- to represent the row in foreign keys.
- to organize storage for the relation.
- as a basis for indexes and other structures to facilitate searching in storage.

A **null value** occurs when no value has been given to an *attribute*. The problem with a null value is that its meaning is ambiguous. It can mean that no value is appropriate, that a value is appropriate but has not yet been chosen, or that a value is appropriate and has been chosen but is unknown to the user. It is possible to eliminate null values by requiring attribute values. Three possible **interpretations of a null value**:

- Value not appropriate
- Value known to be blank
- Value appropriate and unknown

A **functional dependency** occurs when the value of one attribute (or set of attributes) determines the value of a second attribute (or set of attributes). The attribute on the left side of a functional dependency is called the determinant. One way to view the purpose of a relation is to say that the relation exists to store instances of functional dependencies. Another way to define a primary (and candidate) key is to say that such a key is an attribute that functionally determines all the other attributes in a relation.

    CookieCost = NumberOfBoxes x 5

A more general way to express the relationship between `CookieCost` and `NumberOfBoxe`x is to say that `CookieCost` depends upon `NumberOfBoxes`. More formally we can say that CookieCost is **functional dependent** on `NumberOfBoxes`. Such a statement is called a **functional dependency**, where `NumberOfBoxes` is **dererminant**, and can be written as follows:

    NumberOfBoxes -> CookieCost
  
**Normalization** is the process of evaluating a relation and, when necessary, breaking the relation into two or more relations that are better designed and said to be well formed. According to normalization theory, a relation is poorly structured if it has a functional dependency that does not involve the primary key. Specifically, in a well-formed relation, every determinant is a candidate key.

      # Before normalization
      ADVISER_LIST (AdviserID, AdviserName, Department, Phone, Office, StudentNumber, StudentName)
      
      # After normalization
      StudentNumber → (AdviserID, AdviserName, Department, Phone, Office, StudentName)
      ADVISER_LIST (AdviserID, AdviserName, Department, Phone, Office, StudentNumber, StudentName)
                                                                       -------------
A process for normalizing relations into BNCF is shown, and a discussion of multivalued dependencies and 4NF is found. According to this process, relations that have normalization problems are divided into two or more relations that do not have such problems. Foreign keys are established between the old and new relations, and referential integrity constraints are created.

A primary key and its related foreign key must have the same **domain of values**. In very simple terms, the domain of values are the range of valid values an attribute (column) can have. Having the same domain of values is just a fancy way to say the two attributes (columns) have the same **allowable** values. It means the attributes represent the same thing even though they are are in different relations (tables). 

## Structured Query Language

**Structured Query Language** (SQL) is a data sublanguage that has constructs for defining and processing a database. SQL can be embedded into: VBScript (scripting languages), or into programming languages, such as *Java* and *C#*. SQL statements can be processed from a command window. SQL has several components, two of which are discussed here:

- **data definition language (DDL)** is used for creating database tables and other structures.
- **data manipulation language (DML)** is used to query and modify database data. 

SQL was developed by IBM and has been endorsed as a national standard by the American National Standards Institute **(ANSI)**. There have been several versions of SQL. This discussion is based on SQL-92, but later versions exist that have added, in particular, support for Extensible Markup Language **(XML)**. Modern DBMS products provide graphic facilities for accomplishing many of the tasks that SQL does. Use of SQL is mandatory for programmatically creating SQL statements.

> Microsoft Access 2013 uses a variant of SQL known as **ANSI-89 SQL**, or Microsoft Jet SQL, which differs significantly from **SQL-92**. Not all SQL statements written in SQL-92 and later versions run in Access ANSI-89 SQL.

The **SQL CREATE TABLE** statement is used to create relations. Each column is described in three parts: 

- column name, 
- the data type
- optional column constraints. 

Column constraints considered in this chapter are PRIMARY KEY, FOREIGN KEY, NULL, NOT NULL, and UNIQUE. The DEFAULT keyword (not considered a constraint) is also considered. If no column constraint is specified, the column is set to NULL.

Standard data types:

- Char
- VarChar
- Integer
- Numeric
- DateTime (supplemented by DBMS vendors).

If a primary key has only one column, you can define it by using the primary key constraint. Another way to define a primary key is to use the table constraint. You can use such constraints to define single-column and multicolumn primary keys, and you can also implement referential integrity constraints by defining foreign keys. Foreign key definitions can specify that updates and deletions should cascade.

After the tables and constraints are created, you can add data by using The **SQL INSERT** statement and you can query data by using The **SQL SELECT** statement. The basic format of the SQL SELECT statement is SELECT (column names or the asterisk symbol [*]), **FROM** (table names, separated by commas if there is more than one), **WHERE** (conditions). You can use SELECT to obtain specific columns, specific rows, or both.

    -- Select all from student table 
    SELECT *  FROM tblStudent;
    
    -- Select StudentNum, LastName, FirstName, SSN from student table
    SELECT StudentNum, LastName, FirstName, SSN FROM tblStudent;

Conditions after **WHERE** require single quotes around values for Char and VarChar columns. However, single quotes are not used for Integer and Numeric columns. You can specify compound conditions with **AND** and **OR**. You can use sets of values with **IN** (match any in the set) and NOT IN (not match any in the set). You can use the wildcard symbols _ and % (? and * in Microsoft Access) with LIKE to specify a single unknown character or multiple unknown characters, respectively. You can use **IS NULL** to test for null values.

You can sort results by using the **ORDER BY** command. The five SQL built-in functions are **COUNT, SUM, MAX, MIN, and AVG**. SQL can also perform mathematical calculations. You can create groups by using **GROUP BY**, and you can limit groups by using **HAVING**. If the keywords WHERE and HAVING both occur in an SQL statement, WHERE is applied before HAVING.

You can query multiple tables by using either subqueries or joins. If all the result data come from a single table, then subqueries can be used. If results come from two or more tables, then joins must be used. The **JOIN ... ON** syntax can be used for joins. Rows that do not match the join conditions do not appear in the results. Outer joins can be used to ensure that all rows from a table appear in the results.

You can modify data by using The **SQL UPDATE ... SET** statement and delete data by using The **SQL DELETE** statement. The **SQL UPDATE** and SQL DELETE statements can easily cause disasters, so the commands must be used with great care.

You can remove tables (and their data) from a database by using the **SQL DROP TABLE** statement. You can remove constraints by using the **SQL ALTER TABLE DROP CONSTRAINT** command. You can modify tables and constraints by using The **SQL ALTER TABLE** statement. Finally, you can use the **CHECK** constraint to validate data values.

## Data Modeleing and Entity Relationship Diagram (ERD)

The process of developing a database system consists of three stages: 

- **Requirements analysis**:
  - interview users
  - document systems requirements
  - construct a data model
  - create prototypes of selected portions of the future system
- **Component design**:
  - transform the data model into a relational database design
- **Implementation**:
  - construct the database
  - fill it with data
  - create queries
  - create forms
  - create reports
  - create application programs.

In addition to creating a data model, you must also determine data-item data types, properties, and limits on data values. You also need to document **business rules** that constrain database activity.

The **entity-relationship (E-R) model** is the most popular tool used to develop a **data model**. With the **E-R model**, entities, which are identifiable things of importance to the users, are defined. All the entities of a given type form an entity class. A particular entity is called an instance. Attributes describe the characteristics of entities, and one or more attributes identify an entity. Identifiers can be unique or nonunique.

Relationships are associations among entities. The E-R model explicitly defines relationships. Each relationship has a name, and there are relationship classes as well as relationship instances. According to the original specification of the E-R model, relationships may have attributes; however, this is not common in contemporary data models.

The degree of a relationship is the number of entities participating in the relationship. Most relationships are binary. The three types of binary relationships are 1:1, 1:N, and N:M. A recursive relationship occurs when an entity has a relationship to itself.

In traditional E-R diagrams, such as the traditional E-R model, entities are shown in rectangles and relationships are shown in diamonds. The maximum cardinality of a relationship is shown inside the diamond. The minimum cardinality is indicated by a hash mark or an oval.

A weak entity is one whose existence depends on another entity; an entity that is not weak is called a strong entity. In this text, we further define a weak entity as an entity that logically depends on another entity. An entity can have a minimum cardinality of one in a relationship with another entity and not necessarily be a weak entity. ID-dependent entities must include the identifier of the entity on which the ID-dependent entity depends as part of the identifier of the ID-dependent entity.

When a data model has one or more attributes that seem to be associated with a relationship between two entities rather than with either of the entities themselves, an associative entity (also called an association entity) must be added to the data model. Each of the original entities will have a 1:N relationship with the associative entity, which will have a composite primary key consisting of the two primary keys of the original entities. The associative entity will be ID-dependent on both of the original entities.

The extended E-R model introduced the concept of subtypes. A subtype entity is a special case of another entity known as its supertype. In some cases, an attribute of the supertype, called a discriminator, indicates which of the subtypes is appropriate for a given instance. Subtypes can be exclusive (the supertype relates to at most one subtype) or inclusive (the supertype can relate to one or more subtypes). The identifier of the subtype is the identifier of the supertype.

This text’s E-R diagrams use the Information Engineering Crow’s Foot E-R model. You should be familiar with diagrams of that style, but you should also realize that when creating a database design no fundamental difference exists between the traditional style and this style. When creating a data model, it is important to document **business rules** that constrain database activity.

After E-R models are completed, they must be evaluated. You can show the data model, or portions of the data model, directly to the users for evaluation. This requires the users to learn how to interpret an E-R diagram. Sometimes, instead of showing users a data model you may create prototypes that demonstrate the consequences of the data model. Such prototypes are easier for users to understand.

## Database design

A **database design** is a set of database specifications that can actually e implemented as a database in a DBMS. System analysis and design often identify three design schemas:

- Conceptual design (conceptual schema)
- Logical design (logical schema)
- Physical design (physical schema)

To transform an E-R data model into a relational database design, you create a table for each entity. The attributes of the entity become the columns of the table, and the identifier of the entity becomes the primary key of the table. For each column, you must define data types, null status, any default values, and any data constraints. You then apply the normalization process to each table and create additional tables, if necessary. In some cases, you need to denormalize a table. When you do, the table will have insertion, update, and deletion problems.

Steps for transforming a **data model** into database design:

- Create a table for each entity in the data model
  - Specify primary key(consider surrogate keys as appropriate)
  - Specify properties for each column: Data Types, Null status, Default value(if any), Data constraints(if any)
  - Make sure that each of the tables is properly normalized
- Create the relationships between tables by placing foreign keys
  - Strong entity relationships (1:1, 1:N, N:M)
  - ID-dependent and non-ID-dependent weak entity relations
  - Subtypes
  - Recursive (1:1, 1:N, N:M)

Steps of **representing entities** with the Relational Model:

- Define a table for each entity and give that table the same name as the entity.
  - Primary key of the relation the identifier of the entity
- Create a column in the relation for each attribute in the entity
- Apply normalization process to remove any normalization problems

Column **properties**:

- Data types, usually set whan the table is actually created in the database
- Null Status: NoT NULL or NULL
- Default Values, value that the DBMS automatically supplies when a new row is created
- Data Constraints The data values in some columns may be subject to restrictions on the values that can exist in those columns. 

**Denormalization** makes sense if the benefit of not normalizing outweighs the possible problems that could be caused by such modifications.

**Weak entities** are represented by a table. ID-dependent entities must include the key columns of the tables on which they depend, as well as of the identifiers of the entities themselves. Non–ID-dependent entities must have their existence dependence recorded as business rules.

**Supertypes** and **subtypes** are each represented by separate tables. The identifier of the supertype entity becomes the primary key of the supertype table, and the identifiers of the subtype entities become the primary keys of the subtype tables. The primary key of each subtype is also the same primary key that is used for the supertype, and the primary key of each subtype serves as a foreign key that links the subtype back to the supertype.

The **E-R model** has three types of binary relationships: **1:1, 1:N, and N:M**. To represent a 1:1 relationship, you place the key of one table into the other table. To implement the 1:1 relationship, the specified foreign key must be constrained as UNIQUE. To represent a 1:N relationship, you place the key of the parent table in the child table. Finally, to represent an M:N relationship, you create an intersection table that contains the keys of the other two tables.

**Recursive relationships** are relationships in which the participants in the relationship arise from the same entity class. The three types of recursive relationships are 1:1, 1:N, and N:M. These types of relationships are represented in the same way as are their equivalent nonrecursive relationships. For 1:1 and 1:N relationships, you add a foreign key to the relation that represents the entity. For an N:M recursion, you create an intersection table that represents the M:N relationship.

## Database administration

**Database administration** is a business function that involves managing a database in order to maximize its value to an organization. The conflicting goals of protecting the database and maximizing its availability and benefit to users must be balanced using good administration.

All databases need database administration. The database administration for small, personal databases is informal; database administration for large, multiuser databases can involve an office and many people. DBA can stand for *database administration* or *database administrator.*  Three basic database administration functions are necessary: 

- Concurrency control
- Security
- Backup & Recovery

The goal of **concurrency control** is to ensure that one user’s work does not inappropriately influence another user’s work. No single concurrency control technique is ideal for all circumstances. Trade-offs need to be made between the *level of protection* and *data throughput*.

A **transaction**, or logical unit of work, is a series of actions taken against a database that occur as an atomic unit; either all of them occur or none of them do. The activity of concurrent transactions is interleaved on the database server. In some cases, updates can be lost if concurrent transactions are not controlled. Another concurrency problem concerns *inconsistent reads*:

- A **dirty read** occurs when one transaction reads a changed record that has not been committed to the database. 
- A **nonrepeatable read** occurs when one transaction rereads data it has previously read and finds modifications or deletions caused by another transaction. 
- A **phantom read** occurs when a transaction rereads data and finds new rows that were inserted by a different transaction.

To avoid concurrency problems, database elements are locked. Implicit locks are placed by the DBMS; explicit locks are issued by the application program. The size of a locked resource is called **lock granularity**. An exclusive lock prohibits other users from reading the locked resource; a shared lock allows other users to read the locked resource but not to update it.

Two transactions that run concurrently and generate results that are consistent with the results that would have occurred if the transactions had run separately are referred to as serializable transactions. **Two-phase locking**, in which locks are acquired in a growing phase and released in a shrinking phase, is one scheme for serializability. A special case of two-phase locking is to acquire locks throughout the transaction but not to free any lock until the transaction is finished.

**Deadlock**, or the deadly embrace, occurs when two transactions are each waiting on a resource that the other transaction holds. Deadlock can be prevented by requiring transactions to acquire all locks at the same time. When deadlock occurs, the only way to cure it is to abort one of the transactions and back out of partially completed work.

**Optimistic locking** assumes that no transaction conflict will occur and then deals with the consequences if it does. **Pessimistic locking** assumes that conflict will occur and so prevents it ahead of time with locks. In general, optimistic locking is preferred for the Internet and for many intranet applications.

Most application programs do not explicitly declare locks. Instead, they mark transaction boundaries with SQL transaction control statements—such as BEGIN, COMMIT, and ROLLBACK statements—and declare the concurrent behavior they want. The DBMS then places locks for the application that will result in the desired behavior. An ACID transaction is one that is atomic, consistent, isolated, and durable. Durable means that database changes are permanent. Consistency can refer to either statement-level or transaction-level consistency. With transaction-level consistency, a transaction may not see its own changes.

The three types of data read problems that can occur are dirty read, nonrepeatable read, and phantom read. These problems are summarized below: 

Data Read Problem Type | Definition
-----------------------|----------------------
Dirty read             | The transaction reads a row that has been changed, but the change has not been committed. If the change is rolled back, the transaction has incorrect data.
Nonrepeatable Read     | The transaction rereads data that has been changed, and finds changes due to committed transactions.
Phantom Read           | The transaction rereads data and finds new rows inserted by a committed transaction.

The 1992 SQL standard defines four transaction isolation levels: read uncommitted, read committed, repeatable read, and serializable. The characteristics of each are summarized below:

Problem Type       | Read Uncommited | Read Committed | Repeatable Read | Serializable
-------------------|-----------------|----------------|-----------------|-------------
Dirty Read         | Possible        | Not possible   | Not possible    | Not possible
Nonrepeatable Read | Possible        | Possible       | Not possible    | Not possible
Phantom Read       | Possible        | Possible       | Possible        | Not possible

A **cursor** is a pointer into a set of records. Four cursor types are prevalent: forward only, static, keyset, and dynamic. Developers should select isolation levels and cursor types that are appropriate for their application workload and for the DBMS product in use.

The goal of **database security** is to ensure that only authorized users can perform authorized activities at authorized times. To develop effective database security, the processing rights and responsibilities of all users must be determined.

DBMS products provide security facilities. Most involve the declaration of users, groups, objects to be protected, and permissions or privileges on those objects. Almost all DBMS products use some form of user name and password security. DBMS security can be augmented by application security.

In the event of system failure, the database must be **restored** to a usable state as soon as possible. Transactions in process at the time of the failure must be reapplied or restarted. Although in some cases recovery can be done by reprocessing, the use of logs and before-images and after-images with rollback and rollforward is almost always preferred. Checkpoints can be made to reduce the amount of work that needs to be done after a failure.

In addition to concurrency control, security, and backup and recovery, a DBA needs to ensure that a system exists to gather and record errors and problems. The DBA works with the development team to resolve such problems on a prioritized basis and also to evaluate features and functions of new releases of the DBMS. In addition, the DBA needs to create and manage a process for controlling the database configuration so that changes to the database structure are made with a community-wide view. Finally, the DBA is responsible for ensuring that appropriate documentation is maintained about database structure, concurrency control, security, backup and recovery, and other details that concern the management and use of the database.

## Big Data, Data Warehouses, and Business Intelligence Systems

**Business intelligence (BI) systems** assist managers and other professionals in the analysis of current and past activities and in the prediction of future events. BI applications are of two major types: *reporting applications* and *data mining applications*. Reporting applications make elementary calculations on data. Data mining applications use sophisticated mathematical and statistical techniques.

BI applications obtain data from three sources: *operational databases*, *extracts of operational databases*, and *purchased data*. A BI system sometimes has its own DBMS, which may or not be the operational DBMS. *Characteristics of reporting and data mining applications* are listed in below:

- Reporting
  - Filter, sort, group, and make simple calculations
  - Summarize current status
  - Compare current status to past or predicted status
  - Classify entities (customers, products, employees, etc.)
  - Report delivery crucial
- Data Mining
  - Often employ sophisticated statistical and mathematical techniques
  - User for:
    - What-if analyses
    - Predictions
    - Decisions
  - Results often incorporated into other report or system 

Direct reading of operational databases is not feasible for any but the smallest and simplest BI applications and databases—for several reasons. Querying operational data can unacceptably slow the performance of operational systems, operational data have problems that limit their usefulness for BI applications, and BI system creation and maintenance require programs, facilities, and expertise that are normally not available for an operational database.

Operational data may have problems. Because of the problems with operational data, many organizations have chosen to create and staff data warehouses and data marts. **Extract, transform, and load (ETL)** systems are used to extract data from operational systems; transform the data and load them into data warehouses; and maintain metadata that describes the source, format, assumptions, and constraints about the data. A **data mart** is a collection of data that is smaller than that held in a data warehouse and that addresses a particular component or functional area of the business. In the enterprise data warehouse distributes data to three smaller data marts, each of which services the needs of a different aspect of the business.

                                                ------------------------------------------
                                                | Web  |      |         BI Tools         |
                                                | Log  | ---> |   for Web-Click-Stream   |
                                                | Data |      |         Analysis         |--> Web Page Design Features
                                                ------------------------------------------
                        Data        Data        |        Web Sales data Mart             |
                      Warehouse   Warehouse     ------------------------------------------
                       Metadata    Database   /  
                         \          /        / 
                          \        /        /   ------------------------------------------
                           \      /        /    | Store  |      |       BI Tools         |
                            \    /        /     | Sales  | ---> |      for Store         |       Market Basket
    Data Producers --> Data warehouse DBMS ---- | Data   |      |      Managment         |--> Analysis for Sales 
                                          \     ------------------------------------------
                                           \    |       Store Sales Data mart            |
                                            \   ------------------------------------------
                                             \
                                              \
                                                ------------------------------------------
                                                | Inventory |     |       BI Tools       |
                                                |  Histiry  | --> | for Web-Click-Stream |      Inventory Layout
                                                |   Data    |     |       Analysis       |--> for Optimal Item
                                                ------------------------------------------          Picking
                                                |        Web Sales data Mart             |
                                                ------------------------------------------

Operational databases and dimensional databases have different characteristics, as shown below:

Operational Database                             | Dimensional Database  
-------------------------------------------------|-------------------------------------------------
Used for structured transaction data processing  | Used for unstructured analytical data processing
Current data are used                            | Current and historical data are used
Data are inserted, updated, and deleted by users | Data are loaded and updated systematically

**Dimensional databases** use a star schema with a fully normalized fact table that connects to dimension tables that may be non-normalized. Dimensional databases must deal with slowly changing dimensions, and therefore a time dimension is important in a dimensional database. Fact tables hold measures of interest, and dimension tables hold attribute values used in queries. The star schema can be extended with additional fact tables, dimension tables, and conformed dimensions.

The purpose of a reporting system is to create meaningful information from disparate data sources and to deliver that information to the proper users on a timely basis. Reports are produced by sorting, filtering, grouping, and making simple calculations on the data. RFM analysis is a typical reporting application. Customers are grouped and classified according to how recently they have placed an order (R), how frequently they order (F), and how much money (M) they spend on orders. An RFM report can be produced using SQL statements.

**Online Analytical Processing** (OLAP) reporting applications enable users to dynamically restructure reports. A measure is a data item of interest. A dimension is a characteristic of a measure. An OLAP report, or OLAP cube, is an arrangement of measures and dimensions. With OLAP, users can drill down and exchange the order of dimensions.

A **distributed database** is a database that is stored and processed on more than one computer. A **replicated database** is one in which multiple copies of some or all of the database are stored on different computers. A **partitioned database** is one in which different pieces of the database are stored on different computers. A distributed database can be replicated and distributed.

Distributed databases pose processing challenges. If a database is updated on a single computer, then the challenge is simply to ensure that the copies of the database are logically consistent when they are distributed. However, if updates are to be made on more than one computer, the challenges become significant. If the database is partitioned and not replicated, then challenges occur if transactions span data on more than one computer. If the database is replicated and if updates occur to the replicated portions, then a special locking algorithm called distributed two-phase locking is required. Implementing this algorithm can be difficult and expensive.

Objects consist of methods and properties or data values. All objects of a given class have the same methods, but they have different property values. Object persistence is the process of storing object property values. Relational databases are difficult to use for object persistence. Some specialized products called object-oriented DBMSs were developed in the 1990s but never received commercial acceptance. Oracle and others have extended the capabilities of their relational DBMS products to provide support for object persistence. Such databases are referred to as object-relational databases.

The **NoSQL movement** (now often read as “not only SQL”) is built upon the need to meet the **Big Data** storage needs of companies such as Amazon.com, Google, and Facebook. The tools used to do this are nonrelational DBMSs know as structured storage. An early example was Bigtable, and a more recent popular example is Cassandra. These products use a non-normalized table structure built on columns, super columns, column families, and super column families tied together by rowkey values from a keyspace. Data processing of the very large data sets found in Big Data is done by the **Map Reduce** process, which breaks a data processing task in many parallel tasks done by many computers in the cluster and then combines these results to produce a final result. An emerging product that is supported by Microsoft and Oracle Corporation is the **Hadoop Distributed File System** (HDFS), with its spinoffs HBase, a nonrelational storage component, and Pig, a query language.

## Glossary

**.NET Framework (.NET)** Microsoft’s comprehensive application development platform. It includes such components as ADO.NET and ASP.NET.

`<?php and ?>` The symbols used to indicate blocks of PHP code in Web pages.

## A

**ACID transaction** A transaction that is *atomic*, *consistent*, *isolated*, and *durable*. An atomic transaction is one in which a set of database changes are committed as a unit; either all of them are completed or none of them are. A consistent transaction is one in which all actions are taken against rows in the same logical state. An isolated transaction is one that is protected from changes by other users. A durable transaction is one that, once committed to a database, is permanent regardless of subsequent failure. There are different levels of consistency and isolation. See transaction-level consistency and statement-level consistency. See also transaction isolation level.

**Active Server Pages (ASP)** A combination of HTML and scripting language statements. Any statement included in <% . . . %> is processed on the server. Used with Internet Information Server (IIS).

**Active Data Objects (ADO)** An implementation of OLE DB that is accessible via object- and non-object-oriented languages. It is used primarily as a scripting-language (JScript, VBScript) interface to OLE DB.

**ADO.NET** A data access technology that is part of Microsoft’s .NET initiative. ADO.NET provides the capabilities of ADO, but with a different object structure. ADO.NET also includes new capabilities for the processing of datasets.

**After-image** A record of a database entity (normally a row or a page) after a change. Used in recovery to perform rollforward.

**American National Standards Institute (ANSI)** The American standards organization that creates and publishes the SQL standards.

**AMP** An abbreviation for Apache, MySQL, and PHP/Pearl/Python. See Apache Web Server and PHP.

**Anomaly** In normalization, an undesirable consequence of a data modification. With an insertion anomaly, facts about two or more different themes must be added to a single row of a relation. With a deletion anomaly, facts about two or more themes are lost when a single row is deleted.

**Apache Web Server** A popular Web server that runs on most operating systems, particularly Windows and Linux.

**Application program interface (API)** The set of objects, methods, and properties that is used to access the functionality of a program such as a DBMS.

**Association relationship** In database design, a table pattern where an intersection table contains additional attributes beyond the attributes that make up the composite primary key.

**Associative entity** Also called an association entity, this is an entity that represents the combination of at least two other objects and that cont MBains data about that combination. It is often used in contracting and assignment applications.

**Asterisk (*)** A wildcard character used in Microsoft Access queries to represent one or more unspecified characters. See SQL percent sign (%) wildcard character.

**Atomic transaction** A group of logically related database operations that are performed as a unit. Either all the operations are performed or none of them are.

**Attribute** (1) A value that represents a characteristic of an entity. (2) A column of a relation. 

## B

**Before-image** A record of a database entity (normally a row or a page) before a change. Used in recovery to perform rollback.

**Big data** The current term for the enormous datasets created by Web applications, such as search tools (e.g., Google and Bing), and by Web 2.0 social networks, such as Facebook, LinkedIn, and Twitter.

**Bigtable** A nonrelational unstructured data store developed by Google.

**Binary relationship** A relationship between exactly two entities or tables.

**Boyce-Codd Normal Form (BCNF)** A relation in third normal form in which every determinant is a candidate key.

**Business intelligence (BI) systems** Information systems that assist managers and other professionals in analyzing current and past activities and in predicting future events. Two major categories of BI systems are reporting systems and data mining systems.

**Business rule** A statement of a policy in a business that restricts the ways in which data can be inserted, updated, or deleted in the database.

## C

**Candidate key** An attribute or a group of attributes that identifies a unique row in a relation. One of the candidate keys is chosen to be the primary key.

**Cardinality** In a binary relationship, the maximum or minimum number of elements allowed on each side of the relationship. The maximum cardinality can be 1:1, 1:N, N:1, or N:M. The minimum cardinality can be optional/optional, optional/mandatory, mandatory/optional, or mandatory/mandatory.

**Cascading deletion** A property of a relationship that indicates that when one row is deleted, related rows should be deleted as well.

**Cascading update** A referential integrity action specifying that when the key of a parent row is updated, the foreign keys of matching child rows should be updated as well.

**Cassandra** A nonrelational unstructured data store from the Apache Software Foundation.

**Checkpoint** The point of synchronization between a database and a transaction log. At the checkpoint, all buffers are written to external storage. (This is the standard definition of checkpoint, but DBMS vendors sometimes use this term in other ways.)

**Child** A row, record, or node on the many side of a one-to-many relationship. See also parent.

**Click-stream data** Data about a customer’s clicking behavior on a Web page; such data are often analyzed by e-commerce companies.

**Column** A logical group of bytes in a row of a relation or a table. The meaning of a column is the same for every row of the relation.

**Commit** A command issued to a DBMS to make database modifications permanent. After the command has been processed, the changes are written to the database and to a log in such a way that they will survive system crashes and other failures. A commit is usually used at the end of an atomic transaction. Contrast this with [rollback]().

**Composite identifier** An identifier of an entity that consists of two or more attributes.

**Composite key** A key of a relation that consists of two or more columns.

**Computed value** A column of a table that is computed from other column values. Values are not stored but are computed when they are to be displayed.

**Concurrent transactions** A condition in which two or more transactions are processed against a database at the same time. In a single-CPU system, the changes are interleaved; in a multi-CPU system, the transactions can be processed simultaneously, and the changes on the database server are interleaved.

**Concurrent update problem** An error condition in which one user’s data changes are overwritten by another user’s data changes. Also called [lost update problem]()

**Confidence** In market basket analysis, the probability of a customer’s buying one product, given that the customer has purchased another product.

**Conformed dimension** In a dimensional database design, a dimension table that has relationships to two or more fact tables.

**Consistency** Two or more concurrent transactions are consistent if the result of their being processed is the same as it would have been had they been processed in some sequential order.

**Consistent** In an ACID transaction, either statement-level or transaction-level consistency. See [ACID transaction](), [consistency](), and [transaction-level consistency]().

**COUNT** In SQL, a function that counts the number of rows in a query result. See [SQL built-in functions]().

**Cube**See [OLAP cube]().

## D

**Data administration** An enterprisewide function that concerns the effective use and control of an organization’s data assets. A person can perform it, but more often it is performed by a group. Specific functions include setting data standards and policies and providing a forum for conflict resolution. See also [database administration]() and [DBA]()

**Data definition language (DDL)** A language used to describe the structure of a database.

**Data manipulation language (DML)** A language used to describe the processing of a database.

**Data mart** A facility similar to a data warehouse, but with a restricted domain. Often, the data are restricted to particular types, business functions, or business units.

**Data mining application** The use of statistical and mathematical techniques to find patterns in database data.

**Data model** (1) A model of users’ data requirements, usually expressed in terms of the entity-relationship model. It is sometimes called a users’ data model. (2) A language for describing the structure and processing of a database.

**Data sublanguage** A language for defining and processing a database intended to be embedded in programs written in another language—in most cases, a procedural language such as COBOL, C#, or Visual Basic. A data sublanguage is an incomplete programming language because it contains only constructs for data definition and processing.

**Data warehouse** A store of enterprise data that is designed to facilitate management decision making. A data warehouse includes not only data, but also metadata, tools, procedures, training, personnel information, and other resources that make access to the data easier and more relevant to decision makers.

**Data warehouse metadata database** The database used to store the data warehouse metadata.

**Database** A self-describing collection of related records or, for relational databases, of related tables.

**Database administration (DBA)** A function that concerns the effective use and control of a particular database and its related applications.

**Database administrator (DBA)** A person or group responsible for establishing policies and procedures to control and protect a database. They work within guidelines set by data administration to control the database structure, manage data changes, and maintain DBMS programs.

**Database backup** A copy of database files that can be used to restore a database to some previous, consistent state.

**Database design** A graphical display of tables (files) and their relationships. The tables are shown in rectangles, and the relationships are shown using lines. A many relationship is shown with a crow’s foot on the end of the line, an optional relationship is depicted by an oval, and a mandatory relationship is shown with hash marks.

**Database management system (DBMS)** A set of programs used to define, administer, and process a database and its applications.

**Database schema** A complete logical view of a database.

**Deadlock** A condition that can occur during concurrent processing in which each of two (or more) transactions is waiting to access data that the other transaction has locked. It also is called the [deadly embrace]().

**Deadly embrace** See [deadlock]()

**Decision support system (DSS)** One or more applications designed to help managers make decisions.

**Degree** In the entity-relationship model, the number of entities participating in a relationship.

**Deletion anomaly** In a relation, the situation in which the removal of one row of a table deletes facts about two or more themes.

**Denormalization** The process of intentionally designing a relation that is not normalized. Denormalization is done to improve performance or security.

**Determinant** One or more attributes that functionally determine another attribute or attributes. In the functional dependency (A, B) → D, C, the attributes (A, B) are the determinant.

**Dimension table** In a star schema dimensional database, the tables that connect to the central fact table. Dimension tables hold attributes used in the organizing queries in analyses such as those of OLAP cubes.

**Dimensional database** A database design that is used for data warehouses and is designed for efficient queries and analysis. It contains a central fact table connected to one or more dimension tables.

**Dirty read** A read of data that have been changed but not yet committed to a database. Such changes may later be rolled back and removed from the database.

**Discriminator** In the entity-relationship model, an attribute of a supertype entity that determines which subtype pertains to the supertype.

**Distributed database** A database that is stored and processed on two or more computers.

**Distributed two-phase locking** A sophisticated form of record locking that must be used when database transactions are processed on two or more machines.

**Document type declaration (DTD)** A set of markup elements that defines the structure of an XML document.

**Domain** (1) The set of all possible values an attribute can have. (2) A description of the format (data type, length) and the semantics (meaning) of an attribute.

**Domain key/normal form (DK/NF)** A relation in which all constraints are logical consequences of domains and keys. In this text, this definition has been simplified to a relation in which the determinants of all functional dependencies are candidate keys.

**Drill down** User-directed disaggregation of data used to break higher-level totals into components.

**Durable** In an ACID transaction, the database changes are permanent. See [ACID transaction]().

**Dynamo** A nonrelational unstructured data store developed by [Amazon.com]().

**Dynamic cursor** A fully featured cursor. All inserts, updates, deletions, and changes in row order are visible to a dynamic cursor.

## E

**Enterprise-class database system** A DBMS product capable of supporting the operating requirement of large organizations.

**Enterprise data warehouse (EDW) architecture** A data warehouse architecture that links specialized data marts to a central data warehouse for data consistency and efficient operations.

**Entity** Something of importance to a user that needs to be represented in a database. In the entity-relationship model, entities are restricted to things that can be represented by a single table. See also [strong entity]() and [weak entity]().

**Entity class** A set of entities of the same type; two examples are EMPLOYEE and DEPARTMENT.

**Entity instance** A particular occurrence of an entity; for example, Employee 100 (an EMPLOYEE) and Accounting Department (a DEPARTMENT).

**Entity-relationship diagram (E-R diagram)** A graphic used to represent entities and their relationships. Entities are normally shown in squares or rectangles, and relationships are shown in diamonds. The cardinality of the relationship is shown inside the diamond.

**Entity-relationship model (E-R model)** The constructs and conventions used to create a model of users’ data. The things in the users’ world are represented by entities, and the associations among those things are represented by relationships. The results are usually documented in an entity-relationship diagram. See also [dat model]().

**Exclusive lock** A lock on a data resource that no other transaction can read or update.

**Explicit lock** A lock requested by a command from an application program.

**Export** A function of a DBMS that writes a file of data in bulk. The file is intended to be read by another DBMS or program.

**Extended entity-relationship (E-R) model** A set of constructs and conventions used to create data models. The things in the users’ world are represented by entities, and the associations among those things are represented by relationships. The results are usually documented in an entity-relationship (E-R) diagram.

**Extensible Markup Language (XML)** A markup language whose tags can be extended by document designers.

**Extract, transform, and load (ETL) system** The portion of a data warehouse that converts operation data to data warehouse data.

## F

**Fact table** The central table in a dimensional database. Its attributes are called measures. See also [measure]().

**Field** (1) A logical group of bytes in a record used with file processing. (2) In the context of the relational model, a synonym for [attribute]().

**Fifth normal form (5NF)** A normal form necessary to eliminate an anomaly where a table can be split apart but not correctly joined back together. Also known as Project-Join Normal Form (PJ/NF).

**File data source** An ODBC data source stored in a file that can be emailed or otherwise distributed among users.

**First normal form (1NF)** Any table that fits the definition of a relation.

**Foreign key** An attribute that is a key of one or more relations other than the one in which it appears.

**Form** A structured on-screen presentation of selected data from a database. Forms are used for both data input and data reading. A form is part of a database application. Compare this with a report.

**Fourth normal form (4NF)** A relation in BCNF in which every multivalued dependency is a functional dependency.

**Functional dependency** A relationship between attributes in which one attribute or group of attributes determines the value of another. The expressions X → Y, “X determines Y,” and “Y is functionally dependent on X” mean that given a value of X, we can determine the value of Y.

## H

**HAS-A relationship** A relationship between two entities or objects that are of different logical types; for example, EMPLOYEE HAS-A(n) AUTO. Contrast this with an IS-A relationship.

**Hadoop Distributed File System (HDFS)** or **Hadoop** An open-source file distribution system that provides standard file services to clustered servers so that their file systems can function as one distributed file system.

**HBase** A nonrelational unstructured data store developed as part of the Apache Software Foundation’s Hadoop project. See [Hadoop Distributed File System (HDFS)]().

**HTML documnet tags** The tags in HTML documents that indicate the structure of the document.

**HTML syntax rules** The standards that are used to create HTML documents.

**Http://localhost** For a Web server, a reference to the user’s computer.

**Hypertext Markup Language (HTML)** A standardized set of text tags for formatting text, locating images and other nontext files, and placing links or references to other documents.

**Hypertext Transfer Protocol (HTTP)** A standardized means for using TCP/IP to communicate over the Internet.

## I

**ID-dependent entity** An entity that cannot logically exist without the existence of another entity. APPOINTMENT, for example, cannot exist without CLIENT to make the appointment. To be an ID-dependent entity, the identifier of the entity must contain the identifier of the entity on which it depends. Such entities are a subset of a weak entity. See also [existence-dependent entity](), and [weak entity]().

**Identifier** In an entity, a group of one or more attributes that determine entity instances.

**Identifying relationship** A relationship that is used when the child entity is ID-dependent upon the parent entity.

**IE Crow’s Foot model** Formally known as the Information Engineering (IE) Crow’s Foot model, it is a system of symbology used to construct E-R diagrams in data modeling and database design.

**Implicit lock** A lock that is placed automatically by a DBMS.

**Inconsistent backup** A backup file that contains uncommitted changes.

**Inconsistent read problem** An anomaly that occurs in concurrent processing in which transactions execute a series of reads that are inconsistent with one another. This problem can be prevented by using two-phase locking and other strategies.

**Index.html** A default Web page name provided by most Web servers.

**Inetpub folder** In Windows operating systems, the root folder for the IIS Web server.

**Information** (1) Knowledge derived from data, (2) data presented in a meaningful context, or (3) data processed by summing, ordering, averaging, grouping, comparing, or other similar operations.

**Information Engineering (IE) model** An E-R model developed by James Martin.

**Integrated Definition 1, Extended (IDEF1X)** A version of the entity-relationship model, adopted as a national standard, but difficult to understand and use. Most organizations use a simpler E-R version like the crow’s foot model.

**Integrated Development Environment (IDE)** An application that provides a programmer or application developer with a complete set of development tools in one package.

**Insertion anomaly** In a relation, a condition that exists when, to add a complete row to a table, one must add facts about two or more logically different themes.

**Internet Information Server (IIS)** A Windows Web server product that processes Active Server Pages (ASP).

**Intersection table** A table (also called a relation) used to represent a many-to-many relationship. It contains the keys of the relations in the relationship. When used to represent entities having a many-to-many relationship, it may have nonkey data if the relationship contains data.

**IS-A relationship** A relationship between a supertype and a subtype. For example, EMPLOYEE and ENGINEER have an IS-A relationship.

## J

**Java Database Connectivity (JDBC)** A standard means for accessing DBMS products from Java. With JDBC, the unique API of a DBMS is hidden, and the programmer writes to the standard JDBC interface.

**Java Server Pages (JSP)** A combination of HTML and Java that is compiled into a servlet.

**Join operation** or **Join** A relational algebra operation on two relations, A and B, that produces a third relation, C. A row of A is concatenated with a row of B to form a new row in C if the rows in A and B meet restrictions concerning their values. For example, A1 is an attribute in A, and B1 is an attribute in B. The join of A with B in which (A1 = B1) will result in a relation, C, having the concatenation of rows in A and B in which the value of A1 is equal to the value of B1. In theory, restrictions other than equality are allowed—a join could be made in which A1 < B1. However, such non-equal joins are not used in practice. Also known as inner join.

## K

**Key** (1) A group of one or more attributes that identify a unique row in a relation. Because relations cannot have duplicate rows, every relation must have at least one key that is the composite of all the attributes in the relation. A key is sometimes called a logical key. (2) With some relational DBMS products, an index on a column used to improve access and sorting speed. It is sometimes called a physical key. 

## L

**LAMP** A version of [AMP]() that runs on Linux.

**Lock**,  or **resource locking** To allocate a database resource to a particular transaction in a concurrent-processing system. The size at which the resource can be locked is known as the lock granularity.

**Lock granularity** The detail possible with a lock.

**Log** A file that contains a record of database changes. The log contains before-images and after-images.

**Logical unit of work (LUW)** An equivalent term for transaction. See [Transaction]().

**Logistic regression** A form of supervised data mining that estimates the parameters of an equation to calculate the odds that a given event will occur.

**Lost update problem** Same as concurrent update problem.

## M

**MapReduce** A big data processing technique that breaks a data analysis into many parallel processes (the Map function) and then combines the results of these processes into one final result (the Reduce function).

**MAX** In SQL, a function that determines the largest value in a set of numbers. See [SQL built-in functions]().

**Maximum cardinality** (1) The maximum number of values that an attribute can have within a semantic object. (2) In a relationship between tables, the maximum number of rows to which a row of one table can relate in the other table.

**Measure** In OLAP, a data value that is summed, averaged, or processed in some simple arithmetic manner.

**Metadate** Data concerning the structure of data in a database stored in the data dictionary. Metadata are used to describe tables, columns, constraints, indexes, and so forth. See also [application metadata]().

**MIN** In SQL, a function that determines the smallest value in a set of numbers. See 

**Minimum cardinality** In a relationship between tables, the minimum number of rows to which a row of one table can relate in the other table.

**Modification anomaly** A situation that exists when the storing of one row in a table records facts about two themes or the deletion of a row removes facts about two themes, or when a data change must be made in multiple rows for consistency.

**Multiple-tier driver** In ODBC, a two-part driver, usually for a client-server database system. One part of the driver resides on the client and interfaces with the application; the second part resides on the server and interfaces with the DBMS.

**Multivalued dependency** A condition in a relation with three or more attributes in which independent attributes appear to have relationships they do not have. Formally, in a relation R (A, B, C), having key (A, B, C) where A is matched with multiple values of B (or of C or of both), B does not determine C, and C does not determine B. An example is the relation EMPLOYEE (EmpNumber, EmpSkill, DependentName), where an employee can have multiple values of EmpSkill and DependentName. EmpSkill and DependentName do not have any relationship, but they do appear to in the relation.

## N

**N:M** An abbreviation for a many-to-many relationship between the rows of two tables.

**Natural join** A join of a relation A having attribute A1 with relation B having attribute B1, where A1 = B1. The joined relation, C, contains either column A1 or B1 but not both.

**NetBeans** A popular open-source integrated development environment (IDE).

**Nonidentifying relationship** In data modeling, a relationship between two entities such that one is not  ID-dependent on the other. See [Identifying relationship]().

**Nonrepeatable reads** A situation that occurs when a transaction reads data it has previously read and finds modifications or deletions caused by a committed transaction.

**Nonunique identifier** An identifier that determines a group of entity instances. See also [unique identifier]().

**Nonunique key** A key that potentially identifies more than one row.

**Normal form** A rule or set of rules governing the allowed structure of relations. The rules apply to attributes, functional dependencies, multivalued dependencies, domains, and constraints. The most important normal forms are 1NF, 2NF, 3NF, BCNF, 4NF, 5NF, and DK/NF.

**Normalization process** The process of evaluating a relation to determine whether it is in a specified normal form and, if necessary, of converting it to relations in that specified normal form.

**Null value** An attribute value that has never been supplied. Such values are ambiguous and can mean the value is unknown, the value is not appropriate, or the value is known to be blank.

## O

**Object persistence** The storage of object data values.

**Object-oriented DBMS (OODBMS)** A type of DBMS that provides object persistence. OODBMSs have not received commercial acceptance.

**Object-oriented programming (OOP)** A programming methodology that defines objects and the interactions between them to create application programs.

**Object-relational database** A database created by a DBMS that provides a relational model interface as well as structures for object persistence. Oracle Database is the leading object-relational DBMS.

**ODBC conformance level** In ODBC, definitions of the features and functions that are made available through the driver’s application program interface (API). A driver API is a set of functions that the application can call to receive services. There are three conformance levels: Core API, Level 1 API, and Level 2 API.

**ODBC data source** In the ODBC standard, a database and its associated DBMS, operating system, and network platform.

**ODBC Data Source Administrator** The application used to create ODBC data sources.

**ODBC Driver** In ODBC, a program that serves as an interface between the ODBC driver manager and a particular DBMS product. Runs on the client machines in a client-server architecture.

**ODBC Driver Manager** In ODBC, a program that serves as an interface between an application program and an ODBC driver. It determines the required driver, loads it into memory, and coordinates activity between the application and the driver. On Windows systems, it is provided by Microsoft.

**OLAP cube** In OLAP, a set of measures and dimensions arranged, normally, in the format of a table.

**OLAP report** The output of an OLAP analysis in tabular format. For example, this can be a Microsoft Excel PivotTable. See 
[OLAP Cube]().

**OLE DB** The COM-based foundation of data access in the Microsoft world. OLE DB objects support the OLE object standard. ADO is based on OLE DB.

**1:1** An abbreviation for a one-to-one relationship between the rows of two tables.

**1:N** An abbreviation for a one-to-many relationship between the rows of two tables.

*8Online Analytical Processing (OLAP)** A technique for analyzing data values, called measures, against characteristics associated with those data values, called dimensions.

**Online Transaction processing (OLTP) system** An operational database system available for, and dedicated to, transaction processing.

**Open Database Connectivity (ODBC)** A standard means for accessing DBMS products. Using ODBC, the unique API of a DBMS is hidden, and the programmer writes to the standard ODBC interface.

**Operational system** A database system in use for the operations of the enterprise, typically an OLTP system. See 

**Optimistic locking** A locking strategy that assumes no conflict will occur, processes a transaction, and then checks to determine whether conflict did occur. If so, the transaction is aborted. See also [dedlock]() and [pessimistic locking]().

**Outer join** A join in which all the rows of a table appear in the resulting relation, regardless of whether they have a match in the join condition. In a left outer join, all the rows in the left-hand relation appear; in a right outer join, all the rows in the right-hand relation appear.

## P

**Parent** A row, record, or node on the one side of a one-to-many relationship. See also [child]().

**Parent mandatory and child mandatory (M-M)** A relationship where the minimum cardinality of the parent is 1 and the minimum cardinality of the child is 1.

**Parent mandatory and child optional (M-O)** A relationship where the minimum cardinality of the parent is 1 and the minimum cardinality of the child is 0.

**Parent optional and child mandatory (O-M)** A relationship where the minimum cardinality of the parent is 0 and the minimum cardinality of the child is 1.

**Parent optional and child optional (O-O)** A relationship where the minimum cardinality of the parent is 0 and the minimum cardinality of the child is 0.

**Partitioned database** A database in which portions of the database are distributed to two or more computers.

**Personal database system** A DBMS product intended for use by an individual or small workgroup. Such products typically include application development tools such as form and report generators in addition to the DBMS. For example, Microsoft Access 2013.

**Pessimistic locking** A locking strategy that prevents conflict by placing locks before processing database read and write requests.

**Phantom read** A situation that occurs when a transaction reads data it has previously read and then finds new rows that were inserted by a committed transaction.

**PHP: Hypertext Processor** A Web page scripting language used to create dynamic Web pages. It now includes an object-oriented programming component and PHP Data Objects (PDO).

**Pig** A query language for nonrelational unstructured data stores developed as part of the Apache Software Foundation’s Hadoop project. See 

**Primary key** A candidate key selected to be the key of a relation.

**Processing rights and responsibilities** Organizational policies regarding which groups can take which actions on specified data items or other collections of data.

**Properties** Same as attributes.

## Q

**Query by Example (QBE)** A style of query interface, first developed by IBM but now used by other vendors, that enables users to express queries by providing examples of the results they seek.

**Question mark (?) wildcard character** A character used in Microsoft Access 2013 queries to represent a single unspecified character.

## R

**Read committed isolation** A level of transaction isolation that prohibits dirty reads but allows nonrepeatable reads and phantom reads.

**Read uncommitted isolation** A level of transaction isolation that allows dirty reads, nonrepeatable reads, and phantom reads to occur.

**Record**, **Row**, **Tuple** (1) A group of fields pertaining to the same entity; used in file-processing systems. (2) In the relational model, a synonym for row and tuple.

**Recovery via reprocessing** Recovering a database by restoring the last full backup, and then recreating each transaction since the backup.

**Recovery via rollback/rollforward** Recovering a database by restoring the last full backup, and then using data stored in a transaction log to modify the database as needed by either adding transactions (roll forward) or removing erroneous transactions (rollback).

**Recursive relationship** A relationship among entities, objects, or rows of the same type. For example, if CUSTOMERs refer other CUSTOMERs, the relationship is recursive.

**A relationship constraint** on foreign key values. A referential integrity constraint specifies that the values of a foreign key must be a proper subset of the values of the primary key to which it refers.

**Relation** A two-dimensional array that contains single-value entries and no duplicate rows. The meaning of the columns is the same in every row. The order of the rows and columns is immaterial.

**Relational model** A data model in which data are stored in relations and relationships between rows are represented by data values.

**Relational database** A database that consists of relations. In practice, relational databases contain relations with duplicate rows. Most DBMS products include a feature that removes duplicate rows when necessary and appropriate. Such removal is not done as a matter of course because it can be time-consuming and expensive.

**Relational schema** A set of relations with referential integrity constraints.

**Relationship** An association between two entities, objects, or rows of relations.

**Relationship cardinality constraint** A constraint on the number of rows that can participate in a relationship. Minimum cardinality constraints determine the number of rows that must participate; maximum cardinality constraints specify the largest number of rows that can participate.

**Relationship class** An association between entity classes.

**Relationship instance** (1) An association between entity instances, (2) a specific relationship between two tables in a database.

**Repeatable reads isolation** A level of transaction isolation that disallows dirty reads and nonrepeatable reads. Phantom reads can occur.

**Replicated database** A database in which portions of the database are copied to two or more computers.

**Report** A formatted set of information created to meet a user’s need.

**Reporting systems** Business intelligence (BI) systems that process data by filtering, sorting, and making simple calculations. OLAP is a type of reporting system.

**RFM analysis** A type of reporting system in which customers are classified according to how recently (R), how frequently (F), and how much money (M) they spend on their orders.

**Rollback** A process that involves recovering a database in which before-images are applied to the database to return to an earlier checkpoint or other point at which the database is logically consistent.

**Rollforward** A process that involves recovering a database by applying after-images to a saved copy of the database to bring it to a checkpoint or other point at which the database is logically consistent.

**Row** A group of columns in a table. All the columns in a row pertain to the same entity. Also known as tuple or record.

## S

**Schema-valid document** An XML document that conforms to XML Schema.

**Scrollable cursor** A cursor type that enables forward and backward movement through a recordset. Three scrollable cursor types discussed in this text are snapshot, keyset, and dynamic.

**Second normal form (2NF)** A relation in first normal form in which all non-key attributes are dependent on all the keys.

**Serializable isolation level** A level of transaction isolation that disallows dirty reads, nonrepeatable reads, and phantom reads.

**Shared lock** A lock against a data resource in which only one transaction can update the data but many transactions can concurrently read those data.

**SQL AND operator** The SQL operator used to combine conditions in an SQL WHERE clause.

**SQL built-in function** In SQL, any of the functions COUNT, SUM, AVG, MAX, or MIN.

**SQL CREATE TABLE statement** The SQL command used to create a database table.

**SQL CREATE VIEW statement** The SQL command used to create a database view.

**SQL FROM clause** The part of an SQL SELECT statement that specifies conditions used to determine which tables are used in a query.

**SQL GROUP BY clause** The part of an SQL SELECT statement that specifies conditions for grouping rows when determining the query results.

**SQL HAVING clause** The part of an SQL SELECT statement that specifies conditions used to determine which rows are in the groupings in GROUP BY clause.

**SQL OR operator** The SQL operator used to specify alternate conditions in an SQL WHERE clause.

*8SQL ORDER BY clause** The part of an SQL SELECT statement that specifies how the query results should be sorted when they are displayed.

**SQL percent sign (%) wildcard character** The standard SQL wildcard character used to specify multiple characters. Microsoft Access uses an asterisk (*) character instead of the underscore character.

**SQL SELECT clause** The part of an SQL SELECT statement that specifies which columns are in the query results.

**SQL SELECT/FROM/WHERE framework** The basic structure of an SQL query (SQL SELECT clause, SQL FROM clause, SQL WHERE clause, SQL ORDER BY clause, SQL GROUP BY clause, SQL HAVING clause, SQL AND operator, ad SQL OR operator).

**SQL SELECT * statement** A variant of an SQL SELECT query that returns all columns for all tables in the query.

**SQL SELECT ... FOR XML statement** A variant of an SQL SELECT query that returns the query results in XML format.

**SQL underscore (_) wildcard character** The standard SQL wildcard character used to specify a single character. Microsoft Access uses a question mark (?) character instead of the underscore character.

**SQL view** A relation that is constructed from a single SQL SELECT statement. SQL views have at most one multivalued path. The term view in most DBMS products, including Microsoft Access, SQL Server, Oracle Database, and MySQL, means SQL view.

**SQL WHERE clause** The part of an SQL SELECT statement that specifies conditions used to determine which rows are in the query results.

**Star schema** In a dimensional database and as used in an OLAP database, the structure of a central fact table linked to dimension tables.

**Statement-level consistency** A situation in which all rows affected by a single SQL statement are protected from changes made by other users during the execution of the statement. 

**Static cursor** A cursor that takes a snapshot of a relation and processes that snapshot.

**Stored procedure** A collection of SQL statements stored as a file that can be invoked by a single command. Usually, DBMS products provide a language for creating stored procedures that augments SQL with programming language constructs. Oracle provides PL/SQL for this purpose, and SQL Server provides Transact-SQL (T-SQL). With some products, stored procedures can be written in a standard language such as Java. Stored procedures are often stored within the database.

**Strong entity** In the entity-relationship model, any entity whose existence in the database does not depend on the existence of any other entity. 

**Structured Query Language (SQL)** A language for defining the structure and processing of a relational database. It can be used as a stand-alone query language, or it can be embedded in application programs. SQL was developed by IBM and is accepted as a national standard by the American National Standards Institute.

**Subquery** A SELECT statement that appears in the WHERE clause of an SQL statement. Subqueries can be nested within each other.

**Subtype entity** In generalization hierarchies, an entity or object that is a subspecies or subcategory of a higher-level type, called a supertype. For example, ENGINEER is a subtype of EMPLOYEE.

**Surrogate key** A unique, system-supplied identifier used as the primary key of a relation. The values of a surrogate key have no meaning to the users and usually are hidden on forms and reports.

**SUM** In SQL, a function that adds up a set of numbers.

**Supertype entity** In generalization hierarchies, an entity or object that logically contains subtypes. For example, EMPLOYEE is a supertype of ENGINEER, ACCOUNTANT, and MANAGER.

## T

**Table** A database structure of rows and columns to create cells that hold data values. Also known as a relation  in a relational database, although strictly only tables that meet specific conditions can be called relations.

**Ternary relationship** A relationship between three entities.

**Third normal form (3NF)** A relation in second normal form that has no transitive dependencies.

**Three-tier architecture** A Web database processing architecture in which the DBMS and the Web server reside on separate computers.

**Time dimension** A required dimension table in a dimensional database. The time dimension allows the data to be analyzed over time.

**Transaction** (1) A group of actions that is performed on the database atomically; either all actions are committed to the database or none of them are. (2) In the business world, the record of an event. 

**Transaction isolation level** The degree to which a database transaction is protected from actions by other transactions. The 1992 SQL standard specifies four isolation levels: read uncommitted, read committed, repeatable read, and serializable.

**Transaction-level consistency** A situation in which all rows affected by any of the SQL statements in a transaction are protected from changes during the entire transaction. This level of consistency is expensive to enforce and is likely to reduce throughput. It might also prevent a transaction from seeing its own changes. 

**Transactional system** A database dedicated to processing transactions such as product sales and orders. It is designed to make sure that only complete transactions are recorded in the database.

**Transitive dependency** In a relation having at least three attributes, such as R (A, B, C), the situation in which A determines B and B determines C, but B does not determine A.

**Trigger** A special type of stored procedure that is invoked by the DBMS when a specified condition occurs. BEFORE triggers are executed before a specified database action, AFTER triggers are executed after a specified database action, and INSTEAD OF triggers are executed in place of a specified database action. INSTEAD OF triggers are normally used to update data in SQL views.

**Two-phase locking** A procedure in which locks are obtained and released in two phases. During the growing phase, the locks are obtained; during the shrinking phase, the locks are released. After a lock is released, no other lock will be granted that transaction. Such a procedure ensures consistency in database updates in a concurrent-processing environment.

**Two-tier architecture** A Web database processing architecture in which the DBMS and the Web server reside on the same computer.

## U

**Unified Modeling Language (UML)**A set of structures and techniques for modeling and designing object-oriented programs and applications. UML is a methodology and a set of tools for such development. UML incorporates the entity-relationship model for data modeling.

**Unique identifier** An identifier that determines exactly one entity instance. 

**Unique key** A key that identifies a unique row.

**User** A person using an application.

**User data source** An ODBC data source that is available only to the user who created it.

**User group** A group of users.

**WAMP** AMP running on a Windows operating system.

**Weak entity** In the entity-relationship model, an entity whose logical existence in a database depends on the existence of another entity. 

**Web Services** A set of XML standards that enable applications to consume each other’s services using Internet technology.

**World Wide Web Consortium (W3C)** The group that creates, maintains, revises, and publishes standards for the World Wide Web including HTML, XML, and XHMTL.

**wwwroot folder** The root folder or directory of a Web site on a Microsoft IIS Web server.

**XHTML** The Extensible Hypertext Markup Language. A reformulation of HTML to XML standards of well-formed documents.
