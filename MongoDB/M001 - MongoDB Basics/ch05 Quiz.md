# Ch05 Indexing and Aggregation Pipeline

## Lab: Aggregation Framework
### Problem: What room types are present in the sample_airbnb.listingsAndReviews collection?
Check all answers that apply:

- [ ] Living Room
- [ ] Kitchen
- [x] **Entire home/apt**
- [ ] Apartment
- [x] **Private room**
- [x] **Shared room**
- [ ] House

```
> db.listingsAndReviews.aggregate([ { "$group": { "_id": "$room_type" } }])

{ "_id" : "Private room" }
{ "_id" : "Shared room" }
{ "_id" : "Entire home/apt" }
```
<br/><br/>

## Quiz: Aggregation Framework
### Problem: What are the differences between using aggregate() and find()?
Check all answers that apply:

- [ ] find() allows us to compute and reshape data in the cursor.
- [x] **aggregate() can do what find() can and more.**
- [ ] find() can do what the aggregate() can do and more.
- [x] **aggregate() allows us to compute and reshape data in the cursor.**

```
aggregate() can do what find() can and more.
- This is correct.
- Any find() query can be translated into an aggregation pipeline equivalent, but not every aggregation pipeline can be translated into a find() query.

find() can do what the aggregate() can do and more.
- This is incorrect.
- Any find() query can be translated into an aggregation pipeline equivalent, but not every aggregation pipeline can be translated into a find() query.

find() allows us to compute and reshape data in the cursor.
- This is incorrect.
- This is incorrect, the only way for us to compute and reshape data using find(), is by using the aggregation framework stages within the find() method.

aggregate() allows us to compute and reshape data in the cursor.
- This is correct.
- The aggregation framework allows us to compute and reshape data via using stages like $group, $sum, and others.
```
<br/><br/>


## Quiz 1: sort() and limit()
## Problem: Which of the following commands will return the name and founding year for the 5 oldest companies in the sample_training.companies collection?
Check all answers that apply:

- [ ]
```
db.companies.find({ "name": 1, "founded_year": 1 }
                  ).sort({ "founded_year": 1 }).limit(5)
```

- [ ]
```
db.companies.find({ },{ "name": 1, "founded_year": 1 }
                 ).sort({ "founded_year": 1 }).limit(5)
```

- [x]
```
db.companies.find({ "founded_year": { "$ne": null }},
                  { "name": 1, "founded_year": 1 }
                 ).limit(5).sort({ "founded_year": 1 })
```

- [x]
```
db.companies.find({ "founded_year": { "$ne": null }},
                  { "name": 1, "founded_year": 1 }
                 ).sort({ "founded_year": 1 }).limit(5)
```

### Detailed answer
```
db.companies.find({ "founded_year": { "$ne": null }},
                  { "name": 1, "founded_year": 1 }
                 ).sort({ "founded_year": 1 }).limit(5)
```
- This is correct.
- We first must filter out the documents where the founded year is not null, then project the fields that we are looking for, which is name, and founded_year in this case. Then we sort the cursor in increasing order, so the first results will have the smallest value for the founded_year field. Finally, we limit the results to our top 5 documents in the cursor, thus getting the 5 oldest companies in this collection.

```
db.companies.find({ },{ "name": 1, "founded_year": 1 }
                 ).sort({ "founded_year": 1 }).limit(5)
```
- This is incorrect.
- This command is missing the search criteria, which means that null values will be included. Excluding the null values isn't always necessary, because it isn't best practice to store these types of values in MongoDB anyway. So there are lots of collections out there without null values. However, this collection contains nulls, and we need to exclude them from our cursor, or else they'll be our smallest value when we sort.

```
db.companies.find({ "founded_year": { "$ne": null }},
                  { "name": 1, "founded_year": 1 }
                 ).limit(5).sort({ "founded_year": 1 })
```
- This is correct.
- While the limit() and sort() methods are not listed in the correct order, MongoDB flips their order when executing the query, delivering the results that the question prompt is looking for.


```
db.companies.find({ "name": 1, "founded_year": 1 }
                  ).sort({ "founded_year": 1 }).limit(5)
- This is incorrect.
- It looks like the query filter has the values that the projection part of the find() command should have, and there is no projection used in this command. So this command will return all companies where the name is equal to 1 and the founded_year is also equal to 1, which unfortunately misses the requirements of the question prompt.
```
<br/><br/>


## Quiz 2: sort() and limit()
### Problem: In what year was the youngest bike rider from the sample_training.trips collection born?
Choose the best answer:

- [ ] 2000
- [ ] 1885
- [x] **1999**
- [ ] 1998

### Detailed answer
1999
- This is correct.
- To get this result you need to run the following query. The most important part is to first filter out all empty string values, in order to get actual year values. You don't have to use projection here, but we added it so that it is easier to see the answer. The sort order should be in decreasing order because we're looking for the youngest person, therefore the highest year value. You don't have to add the limit() method to get this result, but we also added it to make it easier to immediately see the result.
```
db.trips.find({ "birth year": { "$ne":"" } },
              { "birth year": 1 }).sort({ "birth year": -1 }).limit(1)
```

1885
- This is incorrect.
- You may have gotten this result if you sorted in increasing order instead of decreasing order.

2000
1998
- These options are incorrect,
- but are close to the correct answer, so they may have made you double check your answer before submitting it.
<br/><br/>


## Quiz: Introduction to Indexes
### Problem: Jameela often queries the sample_training.routes collection by the src_airport field like this:

```
db.routes.find({ "src_airport": "MUC" }).pretty()
```
Which command will create an index that will support this query?
Choose the best answer:

- [ ] db.routes.makeIndex({ "src_airport": 1 })
- [ ] db.routes.generateIndex({ "src_airport": -1 })
- [x] **db.routes.createIndex({ "src_airport": -1 })**
- [ ] db.routes.addIndex({ "src_airport": 1 })

### Detailed Answer
db.routes.createIndex({ "src_airport": -1 })
- This is correct.
- It doesn't really matter whether the index was created in increasing or decreasing order when it is a simple single-field index.

db.routes.makeIndex({ "src_airport": 1 })
- This is incorrect.
- makeIndex() is not a valid MongoDB command.

db.routes.generateIndex({ "src_airport": -1 })
- This is incorrect.
- generateIndex() is not a valid MongoDB command.

db.routes.addIndex({ "src_airport": 1 })
- This is incorrect.
- addIndex() is not a valid MongoDB command.
<br/><br/>


## Quiz: Introduction to Data Modeling
### Problem: What is data modeling?
Choose the best answer:

- [ ] a way to decide whether to store your data in the cloud or locally
- [ ] a way to show off your amazing data to everyone using graphs and illustrations
- [x] **a way to organize fields in a document to support your application performance and querying capabilities**
- [ ] a way to build your application based on how your data is stored

### Detailed Answer
a way to organize fields in a document to support your application performance and querying capabilities
- This is correct.
- Data modeling is a way to organize your data, which includes making decisions about fields, collections, and datatypes that will be used in each collection.

a way to decide whether to store your data in the cloud or locally
- This is incorrect.
- The decision about what type of storage you are going to use pertains more to the area of security and systems engineering and does not relate to data modeling.

a way to build your application based on how your data is stored
- This is incorrect.
- You can build your application however you see fit. When using some databases you may have to build your application around how the data is stored, but that is not the case for MongoDB. Here, you use data modeling to make decisions that work best with your application and not the other way around.

a way to show off your amazing data to everyone using graphs and illustrations
- This is incorrect.
- Showing off data using graphs and illustrations is called data visualization and is not part of data modeling.
<br/><br/>


## Quiz: Upsert
## Problem: How does the upsert option work?
Check all answers that apply:

- [ ] It is used with the update operator, and needs to have its value specified every time that the update operator is called.
- [x] **When upsert is set to true and the query predicate returns an empty cursor, the update operation creates a new document using the directive from the query predicate and the update predicate.**
- [x] **By default upsert is set to false.**
- [x] **When upsert is set to false and the query predicate returns an empty cursor then there will be no updated documents as a result of this operation.**

### Detailed Answer
It is used with the update operator, and needs to have its value specified every time that the update operator is called.
- This is incorrect.
- The upsert option only needs its value specified if you want to change the default false setting to true.

By default upsert is set to false.
- This is correct.
- If the upsert option is not specified, then it will have the value of false by default.

When upsert is set to true and the query predicate returns an empty cursor, the update operation creates a new document using the directive from the query predicate and the update predicate.
- This is correct.
- When upsert is set to true it can perform an insert if the query predicate doesn't return a matching document.

When upsert is set to false and the query predicate returns an empty cursor then there will be no updated documents as a result of this operation.
- This is correct.
- When upsert is set to false an update will happen only when the query predicate is matched with a document from the collection.
<br/><br/>