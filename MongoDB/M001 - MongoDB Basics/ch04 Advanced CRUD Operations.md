# ch04 Advanced CRUD Operations

## Query Operators - Comparison
Connect to the Atlas cluster:
```
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"
```

Switch to this database:
```
use sample_training
```

Find all documents where the tripduration was less than or equal to 70 seconds and the usertype was not Subscriber:
```
db.trips.find({ "tripduration": { "$lte" : 70 },
                "usertype": { "$ne": "Subscriber" } }).pretty()
```

Find all documents where the tripduration was less than or equal to 70 seconds and the usertype was Customer using a redundant equality operator:
```
db.trips.find({ "tripduration": { "$lte" : 70 },
                "usertype": { "$eq": "Customer" }}).pretty()
```

Find all documents where the tripduration was less than or equal to 70 seconds and the usertype was Customer using the implicit equality operator:
```
db.trips.find({ "tripduration": { "$lte" : 70 },
                "usertype": "Customer" }).pretty()
```
<br/><br/>

## Query Operators - Logic
Connect to the Atlas cluster:
```
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"
```

Switch to this database:
```
use sample_training
```

Find all documents where airplanes CR2 or A81 left or landed in the KZN airport:
```
db.routes.find({ "$and": [ { "$or" :[ { "dst_airport": "KZN" },
                                    { "src_airport": "KZN" }
                                  ] },
                          { "$or" :[ { "airplane": "CR2" },
                                     { "airplane": "A81" } ] }
                         ]}).pretty()
```
<br/><br/>


## Expressive Query Operator
Connect to the Atlas cluster:
```
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"
```

Switch to this database:
```
use sample_training
```

Find all documents where the trip started and ended at the same station:
```
db.trips.find({ "$expr": { "$eq": [ "$end station id", "$start station id"] }
              }).count()
```

Find all documents where the trip lasted longer than 1200 seconds, and started and ended at the same station:
```
db.trips.find({ "$expr": { "$and": [ { "$gt": [ "$tripduration", 1200 ]},
                         { "$eq": [ "$end station id", "$start station id" ]}
                       ]}}).count()
```
<br/><br/>

## Array Operators

Find all documents with exactly 20 amenities which include all the amenities listed in the query array:

```
use sample_airbnb

db.listingsAndReviews.find({ "amenities": {
                                  "$size": 20,
                                  "$all": [ "Internet", "Wifi",  "Kitchen",
                                           "Heating", "Family/kid friendly",
                                           "Washer", "Dryer", "Essentials",
                                           "Shampoo", "Hangers",
                                           "Hair dryer", "Iron",
                                           "Laptop friendly workspace" ]
                                         }
                            }).pretty()
```
<br/><br/>

## Array Operators and Projection
Connect to the Atlas cluster:
```
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"
```

Switch to this database:
```
use sample_airbnb
```

Find all documents with exactly 20 amenities which include all the amenities listed in the query array, and display their price and address:
```
db.listingsAndReviews.find({ "amenities":
        { "$size": 20, "$all": [ "Internet", "Wifi",  "Kitchen", "Heating",
                                 "Family/kid friendly", "Washer", "Dryer",
                                 "Essentials", "Shampoo", "Hangers",
                                 "Hair dryer", "Iron",
                                 "Laptop friendly workspace" ] } },
                            {"price": 1, "address": 1}).pretty()
```

Find all documents that have Wifi as one of the amenities only include price and address in the resulting cursor:
```
db.listingsAndReviews.find({ "amenities": "Wifi" },
                           { "price": 1, "address": 1, "_id": 0 }).pretty()
```

Find all documents that have Wifi as one of the amenities only include price and address in the resulting cursor, also exclude ``"maximum_nights"``. **This will be an error:*
```
db.listingsAndReviews.find({ "amenities": "Wifi" },
                           { "price": 1, "address": 1,
                             "_id": 0, "maximum_nights":0 }).pretty()
```

Switch to this database:
```
use sample_training
```

Get one document from the collection:
```
db.grades.findOne()
```

Find all documents where the student in class 431 received a grade higher than 85 for any type of assignment:
```
db.grades.find({ "class_id": 431 },
               { "scores": { "$elemMatch": { "score": { "$gt": 85 } } }
             }).pretty()
```

Find all documents where the student had an extra credit score:
```
db.grades.find({ "scores": { "$elemMatch": { "type": "extra credit" } }
               }).pretty()
```
<br/><br/>


## Array Operators and Sub-Documents
Connect to the Atlas cluster:
```
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"
```

```
use sample_training

db.trips.findOne({ "start station location.type": "Point" })

db.companies.find({ "relationships.0.person.last_name": "Zuckerberg" },
                  { "name": 1 }).pretty()

db.companies.find({ "relationships.0.person.first_name": "Mark",
                    "relationships.0.title": { "$regex": "CEO" } },
                  { "name": 1 }).count()


db.companies.find({ "relationships.0.person.first_name": "Mark",
                    "relationships.0.title": {"$regex": "CEO" } },
                  { "name": 1 }).pretty()

db.companies.find({ "relationships":
                      { "$elemMatch": { "is_past": true,
                                        "person.first_name": "Mark" } } },
                  { "name": 1 }).pretty()

db.companies.find({ "relationships":
                      { "$elemMatch": { "is_past": true,
                                        "person.first_name": "Mark" } } },
                  { "name": 1 }).count()
```
<br/><br/>