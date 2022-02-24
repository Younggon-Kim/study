# Ch05 Indexing and Aggregation Pipeline

## Aggregation Framework

Connect to the Atlas cluster:
```
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"
```

Switch to this database:
```
use sample_airbnb
```

Find all documents that have Wifi as one of the amenities. Only include price and address in the resulting cursor.
```
db.listingsAndReviews.find({ "amenities": "Wifi" },
                           { "price": 1, "address": 1, "_id": 0 }).pretty()
```

Using the aggregation framework find all documents that have Wifi as one of the amenities``*. Only include* ``price and address in the resulting cursor.
```
db.listingsAndReviews.aggregate([
                                  { "$match": { "amenities": "Wifi" } },
                                  { "$project": { "price": 1,
                                                  "address": 1,
                                                  "_id": 0 }}]).pretty()
```

Find one document in the collection and only include the address field in the resulting cursor.
```
db.listingsAndReviews.findOne({ },{ "address": 1, "_id": 0 })
```

Project only the address field value for each document, then group all documents into one document per address.country value.
```
db.listingsAndReviews.aggregate([ { "$project": { "address": 1, "_id": 0 }},
                                  { "$group": { "_id": "$address.country" }}])
```

Project only the address field value for each document, then group all documents into one document per address.country value, and count one for each document in each group.
```
db.listingsAndReviews.aggregate([
                                  { "$project": { "address": 1, "_id": 0 }},
                                  { "$group": { "_id": "$address.country",
                                                "count": { "$sum": 1 } } }
                                ])
```
<br/><br/>


## sort() and limit()
Commands used in this lesson:

Connect to the Atlas cluster:
```
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"

use sample_training

db.zips.find().sort({ "pop": 1 }).limit(1)

db.zips.find({ "pop": 0 }).count()

db.zips.find().sort({ "pop": -1 }).limit(1)

db.zips.find().sort({ "pop": -1 }).limit(10)

db.zips.find().sort({ "pop": 1, "city": -1 })
```
<br/><br/>


## Introduction to Indexes
Commands used in this lesson:

```
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"

use sample_training

db.trips.find({ "birth year": 1989 })

db.trips.find({ "start station id": 476 }).sort( { "birth year": 1 } )

db.trips.createIndex({ "birth year": 1 })

db.trips.createIndex({ "start station id": 1, "birth year": 1 })
```
<br/><br/>


## Introduction to Data Modeling
https://university.mongodb.com/courses/M320/about
https://docs.mongodb.com/manual/core/data-modeling-introduction/
https://www.mongodb.com/blog/post/building-with-patterns-a-summary
<br/><br/>


## Upsert - Update or Insert?
Commands used in this lesson:
```
db.iot.updateOne({ "sensor": r.sensor, "date": r.date,
                   "valcount": { "$lt": 48 } },
                         { "$push": { "readings": { "v": r.value, "t": r.time } },
                        "$inc": { "valcount": 1, "total": r.value } },
                 { "upsert": true })
```
<br/><br/>


