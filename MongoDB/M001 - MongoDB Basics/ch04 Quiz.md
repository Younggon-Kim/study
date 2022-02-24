# Ch04 Advanced CRUD Operations

## Lab 1: Comparison Operators
### Problem: 
How many documents in the sample_training.zips collection have fewer than 1000 people listed in the pop field?
Copy/paste the exact numeric value (without double quotes) of the result that you get into the response field.

Enter answer here:
8065

```
db.zips.find({"pop": {"$lt":1000}}).count()
```
<br/><br/>

## Lab 2: Comparison Operators
### Problem: 
What is the difference between the number of people born in 1998 and the number of people born after 1998 in the sample_training.trips collection?
Enter the exact numeric value of the result that you get into the response field.

Enter answer here:
6
```
db.trips.find({"birth year": {"$eq": 1998}}).count()
12
db.trips.find({"birth year": {"$gt": 1998}}).count()
18
```
<br/><br/>

## Lab 3: Comparison Operators
### Problem:
Using the sample_training.routes collection find out which of the following statements will return all routes that have at least one stop in them?

Check all answers that apply:

- [ ] db.routes.find({ "stops": { "$lt": 0 }}).pretty()
- [ ] db.routes.find({ "stops": { "$gte": 0 }}).pretty()
- [x] **db.routes.find({ "stops": { "$ne": 0 }}).pretty()**
- [x] **db.routes.find({ "stops": { "$gt": 0 }}).pretty()**
<br/><br/>

## Quiz 1: Logic Operators
## Problem:
How many businesses in the sample_training.inspections dataset have the inspection result "Out of Business" and belong to the "Home Improvement Contractor - 100" sector?
Enter the exact numeric value of the result that you get into the response field.

Enter answer here:
4
```
db.inspections.find({"$and": [{"result":"Out of Business"}, {"sector":"Home Improvement Contractor - 100"}]}).count()
4
```
<br/><br/>

## Quiz 2: Logic Operators
### Problem:
Which is the most succinct query to return all documents from the sample_training.inspections collection where the inspection date is either "Feb 20 2015", or "Feb 21 2015" and the company is not part of the "Cigarette Retail Dealer - 127" sector?

Choose the best answer:

- [x]
```
db.inspections.find(
  { "$or": [ { "date": "Feb 20 2015" },
             { "date": "Feb 21 2015" } ],
    "sector": { "$ne": "Cigarette Retail Dealer - 127" }}).pretty()
```

- [ ]
```
db.inspections.find(
  { "$and": [
      { "$or": [
                 { "date": "Feb 20 2015" },
                 { "date": "Feb 21 2015" } ] },
      {"sector": { "$ne":"Cigarette Retail Dealer - 127" }}]
  }).pretty()
```

- [ ]
```
db.inspections.find(
  { "$or": [ { "date": "Feb 20 2015" },
             { "date": "Feb 21 2015" }],
    "$not": { "sector": "Cigarette Retail Dealer - 127" }}).pretty()
```
<br/><br/>


## Lab 1: Logic Operators
### Problem:
Before solving this exercise, make sure to undo some of the changes that we made to the zips collection earlier in the course by running the following command:
```
db.zips.updateMany({ "city": "HUDSON" }, { "$inc": { "pop": -10 } })
```
How many zips in the sample_training.zips dataset are neither over-populated nor under-populated?
In this case, we consider population of more than 1,000,000 to be over- populated and less than 5,000 to be under-populated.
Copy/paste the exact numeric value (without double quotes) of the result that you get into the response field.

Enter answer here:
11193
```
db.zips.find({"pop":{"$gte": 5000}}, {"pop":{"$lte":1000000}}).count()
11193
```
<br/><br/>

## Lab 2: Logic Operators
### Problem:
How many companies in the sample_training.companies dataset were
either founded in 2004
  - [and] either have the social category_code [or] web category_code,
[or] were founded in the month of October
  - [and] also either have the social category_code [or] web category_code?
Copy/paste the exact numeric value (without double quotes) of the result that you get into the response field.

Enter answer here:
149
```
db.companies.find(
{
    "$or": [
        {
            "founded_year" : 2004, 
            "$or": [
                {"category_code": "social"},
                {"category_code": "web"}
            ]
        },
        {
            "founded_month": 10, 
            "$or": [
                {"category_code": "social"},
                {"category_code": "web"}
            ]
        }
    ],
}
).count()
```
<br/><br/>


## Quiz 1: $expr
### Problem: What are some of the uses for the $ sign in MQL?
Check all answers that apply:

- [ ] $ makes the world go round.
- [ ] $ changes the data type of the given value to a monetary denomination.
- [x] **$ signifies that you are looking at the value of that field rather than the field name.**
- [x] **$ denotes an operator.**

```
$ denotes an operator.
- This is correct.
- All MQL operators have the $ prefix.

$ signifies that you are looking at the value of that field rather than the field name.
- This is correct.
- When $ is used to prefix a field name, it represents the value stored in that field. This is very helpful for expressions that compare fields within the same document.

$ changes the data type of the given value to a monetary denomination.
- This is incorrect.
- While $ does have other awesome uses, changing the data type to some monetary denomination related is not one of them. There is no such data type in BSON.

$ makes the world go round.
- This is incorrect.
- Since this is a course that pertains to MongoDB only and not philosophy or history of pop-music (sorry Liza Minelli) this answer is not correct in the context of MQL and MongoDB in general.
```
<br/><br/>

## Quiz 2: $expr
### Problem: Which of the following statements will find all the companies that have more employees than the year in which they were founded?
Check all answers that apply:

- [x]
```
db.companies.find(
    { "$expr": { "$gt": [ "$number_of_employees", "$founded_year" ]} }
  ).count()
```

- [x]
```
db.companies.find(
    { "$expr": { "$lt": [ "$founded_year", "$number_of_employees" ] } }
  ).count()
```

- [ ]
```
db.companies.find(
  { "$expr": { "$gt": [ "$founded_year", "$number_of_employees" ] } }
).count()
```

- [ ]
```
db.companies.find({ "number_of_employees": { "$gt":  "$founded_year" }
                  }).count()
```
<br/><br/>


## Lab: $expr
### Problem:
How many companies in the sample_training.companies collection have the same permalink as their twitter_username?

Enter answer here:
1299
```
db.companies.find({"$expr": {"$eq": ["$permalink", "$twitter_username"]}}).count()
```
<br/><br/>


## Lab 1: Array Operators
### Problem:
What is the name of the listing in the sample_airbnb.listingsAndReviews dataset that accommodates more than 6 people and has exactly 50 reviews?
Copy/Paste the value of the "name" field into the response field without quotation marks.

Enter answer here:
Sunset Beach Lodge Retreat
```
db.listingsAndReviews.find(
{
    "accommodates": {"$gt": 6},
    "reviews": {"$size": 50}
}
).pretty()
```
<br/><br/>


## Lab 2: Array Operators
### Problem:
To complete this exercise connect to your Atlas cluster using the in-browser IDE space at the end of this chapter.
Using the sample_airbnb.listingsAndReviews collection find out how many documents have the "property_type" "House", and include "Changing table" as one of the "amenities"?
Enter the number of results to the response field.

Enter answer here:
11
```

db.listingsAndReviews.find(
{
    "property_type" : {"$eq": "House"},
    "amenities": {
        "$all": ["Changing table"]
    }
}
).count()
```
<br/><br/>


## Quiz: Array Operators
### Problem:
Which of the following queries will return all listings that have "Free parking on premises", "Air conditioning", and "Wifi" as part of their amenities, and have at least 2 bedrooms in the sample_airbnb.listingsAndReviews collection?

Choose the best answer:

- [x]
```
db.listingsAndReviews.find(
  { "amenities":
      { "$all": [ "Free parking on premises", "Wifi", "Air
        conditioning" ] }, "bedrooms": { "$gte":  2 } } ).pretty()
```

- [ ]
```
db.listingsAndReviews.find(
   { "amenities": [ "Free parking on premises", "Wifi", "Air
                    conditioning" ]},
     "bedrooms": { "$gte": 2 } } ).pretty()
```

- [ ]
```
db.listingsAndReviews.find(
  { "amenities":
      { "$all": [ "Free parking on premises", "Wifi", "Air
                  conditioning" ] },
    "bedrooms": { "$lte": 2 } }).pretty()
```

- [ ]
```
db.listingsAndReviews.find(
  { "amenities": "Free parking on premises", "amenities": "Wifi",
    "amenities": "Air conditioning", "bedrooms": { "$gte": 2 }
  }).pretty()
```
<br/><br/>


## Lab: Array Operators and Projection
### Problem:
How many companies in the sample_training.companies collection have offices in the city of Seattle?
Copy/paste your answer to the response field.

Enter answer here:
117
```
db.companies.find(
{
    "offices": {
        "$elemMatch": {"city": "Seattle"}
    }
}
).count()
```
<br/><br/>


## Quiz: Array Operators and Projection
### Problem:
Which of the following queries will return only the names of companies from the sample_training.companies collection that had exactly 8 funding rounds?

Choose the best answer:

```
db.companies.find(
{ 
    "funding_rounds": 
    { 
        "$size": 8 
    }
},
{ 
    "name": 0, 
    "_id": 1 
}
)
```

```
db.companies.find(
{
    "funding_rounds": 
        {
            "$size": 8 
        }
}, 
{
    "name": 1
}
)
```

```
db.companies.find(
{
    "funding_rounds": 
    { 
        "$size": 8 
    } 
},
{
    "name": 1,
    "_id": 0 
}
)
```
<br/><br/>


## Lab 1: Querying Arrays and Sub-Documents
### Problem: How many trips in the sample_training.trips collection started at stations that are to the west of the -74 longitude coordinate?
Longitude decreases in value as you move west.
Note: We always list the longitude first and then latitude in the coordinate pairs; i.e.
```
<field_name>: [ <longitude>, <latitude> ]
```

Enter answer here:
1928
```
db.trips.find(
{
    "start station location.coordinates.0": {"$lt": -74}
}
).count()
```
<br/><br/>


## Lab 2: Querying Arrays and Sub-Documents
### Problem:
How many inspections from the sample_training.inspections collection were conducted in the city of NEW YORK?

Enter answer here:
18279
```
db.inspections.find(
{
    "address.city" : "NEW YORK"
}
).count()
```
<br/><br/>


## Quiz: Querying Arrays and Sub-documents
### Problem:
Which of the following queries will return the names and addresses of all listings from the sample_airbnb.listingsAndReviews collection where the first amenity in the list is "Internet"?

Choose the best answer:

- [ ]
```
db.listingsAndReviews.find({ "amenities.$0": "Internet" },
                           { "name": 1, "address": 1 }).pretty()
```

- [ ]
```
db.listingsAndReviews.find({ "amenities.[0]": "Internet" },
                           { "name": 1, "address": 1 }).pretty()
```

- [x]
```
db.listingsAndReviews.find({ "amenities.0": "Internet" },
                           { "name": 1, "address": 1 }).pretty()
```