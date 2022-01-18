# Ch01. What is MongoDB?

## What is the MongoDB Database?
Database
- structured way to store and access data

NoSQL database
- related tables of data

NoSQL documentDB
- data in MongoDB is stored as documents

Stored in collections
- Documents are stored in collections of documents

## What is a Document in MongoDB?
Document
- A way to organize and store data as a set of field-value pairs

Field
- a unique identifier for a datapoint.

Value
- data related to a given identifier.
```
{
    <field> : <value>,
    <field> : <value>,
    "name" : "Lakshmi",
    "title": "Team Lead",
    "age" : 26
}
```

Collection
- an organized store of documents in MongoDB, usually with common fields between documents.
- There can be many collections per database and many documents per collection.

Database
- contains multiple collections

## What is MongoDB Atlas?
Atlas
- The Atlas cloud database is our fully managed database built for a wide range of applications with MongoDB at its core.
- Atlas users can deploy clusters, which are groups of servers that store your data.
- Atlas manages the details of creating clusters for you, which simplifies the operational overhead of running and maintaining a database deployment.
- This includes deployment across cloud providers and regions
of your choosing.

Replica Set
- a few connected machines that store the same data to ensure that if something happens to one of the machines the data will remain intact. Comes from the word replicate - to copy something.

Instance
- a single machine locally or in the cloud, running a certain software, in our case it is the MongoDB database.

Cluster
- group of servers that store your data.

