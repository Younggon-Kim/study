## Quiz : Cloud Bigtable
### 1. True or false: Each table in NoSQL databases such as Cloud Bigtable has a single schema that is enforced by the database engine itself.
check
- [x] **False**
- [ ] True
```
Correct! NoSQL databases such as Cloud Bigtable are suitable when all items in the database needn't have their integrity checked by a database schema. Why not? Maybe you want your database items to contain variable fields, or maybe because you simply want your application to manage database integrity.
```
<br/>

### 2. Some developers think of Cloud Bigtable as a persistent hashtable. What does that mean?
- [ ] Each item in the database consists of exactly the same fields, and can be looked up based on a variety of keys.
- [x] **Each item in the database can be sparsely populated, and is looked up with a single key.**
<br/><br/>

## Quiz : Cloud SQL and Cloud Spanner
### 1. Which database service offers transactional consistency at global scale?
- [ ] Cloud SQL.
- [x] **Cloud Spanner.**
```
Correct! Cloud Spanner offers transactional consistency at global scale.
```
<br/>

### 2. Which database service presents a MySQL or PostgreSQL interface to clients?
- [X] **Cloud SQL.**
- [ ] Cloud Spanner.
```
Correct! Each Cloud SQL database is configured at creation time for either MySQL or PostgreSQL. Cloud Spanner uses ANSI SQL 2011 with extensions.
```
<br/>

### 3. Which database service can scale to higher database sizes?
- [ ] Cloud SQL.
- [x] **Cloud Spanner.**
```
Correct! Cloud Spanner can scale to petabyte database sizes, while Cloud SQL is limited by the size of the database instances you choose. At the time this quiz was created, the maximum was 10,230 GB.
```
<br/><br/>

## Quiz : Cloud Datastore
### 1. True or false: Cloud Datastore databases can span App Engine and Compute Engine applications.
- [x] **True.**
- [ ] False.
<br/>

### 2. How are Cloud Datastore and Cloud Bigtable alike? Choose all that are correct (2 correct answers)
- [ ] They both offer SQL-like queries.
- [x] **They are both NoSQL databases.**
- [x] **They are both highly scalable.**
- [ ] They both have a free daily quota.
<br/><br/>

## Quiz : Google Cloud Platform Storage Options
### 1. Your application needs a relational database, and it expects to talk to MySQL. Which storage option is the best choice for your application?
- [x] **Cloud SQL**
- [ ] Bigtable
- [ ] Cloud Storage
- [ ] Cloud Spanner
<br/>

### 2. You manufacture devices with sensors and need to stream huge amounts of data from these devices to a storage option in the cloud. Which Google Cloud Platform storage option is the best choice for your application?
- [x] **Cloud Bigtable**
- [ ] BigQuery
- [ ] Cloud Spanner
- [ ] Cloud Datastore
<br/>

### 3. You are developing an application that transcodes large video files. Which storage option is the best choice for your application?
- [x] **Cloud Storage**
- [ ] Cloud Spanner
- [ ] Cloud Datastore
- [ ] Google Drive
<br/>

### 4. Which statement is true about objects in Cloud Storage?
- [x] **They are immutable, and new versions overwrite old unless you turn on versioning.**
- [ ] They are immutable, and versioned by default.
- [ ] They are immutable unless you turn on versioning.
- [ ] They can be edited in place.
<br/>

### 5. How do the Nearline and Coldline storage classes differ from Multi-regional and Regional? Choose all that are correct (2 responses).
- [x] **Nearline and Coldline assess lower storage fees.**
- [x] **Nearline and Coldline assess additional retrieval fees.**
- [ ] Nearline and Coldline use a differently-architected API.
- [ ] Data in Nearline and Coldline is not retrievable immediately.
- [ ] Nearline and Coldline have lower durability.
<br/>

### 6. You are building a small application. If possible, you'd like this application's data storage to be at no additional charge. Which service has a free daily quota, separate from any free trials?
- [x] **Cloud Datastore**
- [ ] Cloud SQL
- [ ] Bigtable
- [ ] Cloud Spanner
<br/>

### 7. Your application needs to store data with strong transactional consistency, and you want seamless scaling up. Which storage option is the best choice for your application?
- [x] **Cloud Spanner**
- [ ] Cloud Storage
- [ ] Cloud Datastore
- [ ] Cloud SQL
<br/>

### 8. Which GCP storage service is often the ingestion point for data being moved into the cloud, and is frequently the long-term storage location for data?
- [x] **Cloud Storage**
- [ ] Cloud Spanner
- [ ] Local SSD
- [ ] Cloud Datastore
<br/>