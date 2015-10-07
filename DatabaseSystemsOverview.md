### Database Systems Overview

1. > What database models do you know?

  * Hierarchical database model
  * Network model
  * Relational model
  * Object model
  
2. > Which are the main functions performed by a Relational Database Management System (RDBMS)?

  * It stores data in tables. Those tables can be created, altered and deleted. The relations between tables can be set
  * Data in the tables can be also added, changed or removed.
  * Data from these tables can be searched and retrieved using SQL 
  
3. > Define what is "table" in database terms.

  A table is a collection of related data held in a structured format within a database. It consists of columns and rows.
  There is a specified amount of columns and any number of rows.
  
4. > Explain the difference between a primary and a foreign key.

  Primary keys are unique for each row in the table. Foreign keys relate those rows to other tables and the primary keys there.
  
5. > Explain the different kinds of relationships between tables in relational databases.

  * One-to-many relationship: Connects multiple rows in one table to one row in an other. For example a list of cities can have
  relate the cities to the table of countries. There are many cities in one country, but every city belong only to one country.
  
  * Many-to-many relationship: Connects multiple rows in one table to multiple rows in an other. For example if we are asking 
  10 000 persons to name their 3 favorite artists, we would connect every person in one table to multiple artists in an other.
  Every artist can also have multiple likers.
  
  * One-to-one relationship: Every record in one table corresponds only one record in an other. For example if we want to 
  collect a database of people, local and foreigners, each of them has a database-ID, but their identification can be either
  with EGN or Passport number. Storing those in separate tables seem logical, so in one table there are EGNs, another has 
  passport numbers. Each person has only one identification number and no identification number relates to multiple persons.
  
6. > When is a certain database schema normalized? What are the advantages of normalized databases?

  Normalized database schema has all the repetitions removed. It helps a lot in modification. For example in a database of
  different workers from multiple different companies you will be in trouble if all the employees have their company name 
  written in the records and one company changes it's name. In normalized database schema you need to make the update only in
  one place. Removing repetitions also conserves disk space. 
  
7. > What are database integrity constraints and when are they used?

  * Entity Integrity: Every row must have a primary key and they must be unique and not NULL.
  
  * Referential Integrity: Every foreign key must refer to a primary keys of some of the tables in the database. It can be also
  NULL, if the relation is unknown or inexistent.
  
  * Domain integrity: A domain is a set of values of the same type. Each column in a table must be declared upon a defined 
  domain. 
  
  * User-defined integrity: Ensures that every value in a certain column meets a pre-defined condition.
  
  All the other integrity constraints should always be used in relational database systems, only user-defined ones when needed.
  
8. > Point out the pros and cons of using indexes in a database.

  Advantages:
  
  * Speed up searching of values
  
  * In very big databases the increase of speed in retrieving the data usually beats the cons
  
  Disadvantages:
  
  * Adding and deleting data in indexed database is slower
  
  * The index takes up disc space
  
9. > What's the main purpose of the SQL language?

  A standardized language for manipulating relational databases.

10. > What are transactions used for?

  Transactions are sequences of database operations, which are done either fully or not at all. They are used when multiple 
  operations are needed for some activity and it is not acceptable that the first of them would happen and in a case of an 
  error all the others would not. If for example we would have a bit silly system, which transfers money from one account to 
  another. First the money is added to the 2nd account and then this amount is deducted from the first account. Every time 
  when there would be an error after the first addition before the deduction, the total of money in accounts would increase. 
  That would not be acceptable for a bank where those accounts are. In transactional database this would not happen, rollback
  would take care of setting everything to the original state.

11. > What is a NoSQL database?

  Database which is not a relational database. These databases are not following any fixed table schemes. 

12. > Explain the classical non-relational data models.

  The non-relational databases are document-based. Every record is one document with no fixed structure. 
  
13. > Give few examples of NoSQL databases and their pros and cons.

  * MongoDB
    
    Pros: 
    
    * Flexible: MongoDB doesn't require a unified data structure across all objects
    
    * Fast: MongoDB queries can be much faster in some cases, especially since your data is typically all in once place and can 
    be retrieved in a single lookup.
    
    Cons:
    
    * In MongoDB there exists no possibility for joins like in a relational database. Leads to duplicate data.
    
    * Transactions: MongoDB doesn't automatically treat operations as transactions.

  * Redis

    Pros:
  
    * designed for high speed and high availability
  
    * stores data in variety of formats
  
    * mass insertion of data to prime a cache
  
    Cons:
  
    * Complex to configure
  
    * Lots of server administration for monitoring and partitioning and balancing
  
  * Cassandra

    Pros:
  
    * Scalability: built to cope with data management challenges of modern business
  
    * de-centralized: It is possible to add new nodes to server cluster very easy
  
    Cons:
  
    * there is no referential integrity - there is no concept of JOIN connections in Cassandra

    * querying options for retrieving data are very limited
  
    * sorting of data is a design decision; it can be done through one of predefined ways; data can be retrieved back in same
  order; that's all - there is no things like ORDER BY, GROUP BY
