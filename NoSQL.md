# NoSQL

## Introduction

* NoSQL stands for Not Only SQL

* It is non relational

* It has different flavors

* They have flexible schema

* They work well on a distributed cloud

* Examples Include Mongodb, BigQuery, HBase etc

* They are cheaper than SQL

* Scalable

* Types :

  * Key-Value

  * Document

  * Graph

  * BigTable

## Key-Value

 * Hash Based
 * Simplest
 * High performance for simple query
 * Interconnected /Complex Queries - Struggles
 * Horizontally Scalable
 * Use Cases
    * Good for simple queries
    * Shopping websites
* Ex: DynamoDB (AWS), redis

## Document Database

* Store data as JSON, XML etc
* Hierarchical 
* Flexible Input Schemas
* MapReduce for indexing
* Use Cases
  * Event logging
  * blogs
  * meta data
* Ex: mongoDB, IBM Cloudant , couchDB etc

## Column-Family (BigTables)

* Several rows and columns
* columns are grouped together and are called column families
* Rows in same column family are not required to have same columns
* Multidimensional Map
* Save Storage Space
* Horizontal Scaling
* Good for sparse data
* Use Cases
  * Event logging
  * Blogs
  * Counters
* Ex: Hbase, Amazon simpleDB, BigQuery, Cassandra

## Graph databases

* Data is stored in Entity Relationship
* Relation Oriented
* Traversing is fast
* Not good for distributed network
* Good for social network
* Ex: OrientDB, twitter/flockdb, Neo4j

## Data Layer (DBaaS)

* NoSQL is 
  * Good for Operational Data Store
  * Good for cloud architecture
  * Good for Clustered DB
  * Flexible Schema
* Challenges 
  * Integration

## Cloudant [IBM]

* JSON Based
* Scalable
* Similar to MongoDB
* MapReduce
* GUI Based

## JSON

{	

​	"key": value,

​	"nested key": {

​					values

​				}

}

