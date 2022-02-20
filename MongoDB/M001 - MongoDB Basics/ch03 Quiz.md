# Ch03. Creating and Manipulating Documents

## Quiz: ObjectId
### Problem: How does the value of _id get assigned to a document?
Check all answers that apply:

- [x] **It is automatically generated as an ObjectId type value.**
- [ ] When a document is inserted a random field is picked to serve as the _id field.
- [x] **You can select a non ObjectId type value when inserting a new document, as long as that value is unique to this collection.**
- [ ] _id field values are sequential integer values.
<br/><br/>


## Quiz: Insert Errors
### Problem: Select all true statements from the following list:
Check all answers that apply:

- [x] **MongoDB can store duplicate documents in the same collection, as long as their _id values are different.**
- [ ] MongoDB can always store duplicate documents in the same collection regardless of the _id value.
- [ ] If a document is inserted without a provided _id value, then that document will fail to be inserted and cause a write error.
- [ ] There is no way to ensure that duplicate records are not stored in MongoDB.
- [x] **If a document is inserted without a provided _id value, then the _id field and value will be automatically generated for the inserted document before insertion.**
<br/><br/>


## Quiz: Insert Order
### Problem: Which of the following commands will successfully insert 3 new documents into an empty pets collection?
Check all answers that apply:

- [x] **A**
```
db.pets.insert([{ "_id": 1, "pet": "cat" },
                { "_id": 2, "pet": "dog" },
                { "_id": 3, "pet": "fish" },
                { "_id": 3, "pet": "snake" }])
```

- [ ] C
```
db.pets.insert([{ "_id": 1, "pet": "cat" },
                { "_id": 1, "pet": "dog" },
                { "_id": 3, "pet": "fish" },
                { "_id": 4, "pet": "snake" }], { "ordered": true })
```

- [x] **C**
```
db.pets.insert([{ "pet": "cat" }, { "pet": "dog" },
                { "pet": "fish" }])
```

- [x] **D**
```
db.pets.insert([{ "_id": 1, "pet": "cat" },
                { "_id": 1, "pet": "dog" },
                { "_id": 3, "pet": "fish" },
                { "_id": 4, "pet": "snake" }], { "ordered": false })
```
<br/><br/>


## Quiz: Updating Documents
### Problem: MongoDB has a flexible data model, which means that you can have fields that contain documents, or arrays as their values.
Select any invalid MongoDB documents from the given choices:
Check all answers that apply:

- [ ] 
```
{ "_id": 1,
  "pet": "cat",
  "attributes": [ { "coat": "fur",
                    "type": "soft" },
                  { "defense": "claws",
                    "location": "paws",
                    "nickname": "murder mittens" } ],
  "name": "Furball" }
```

- [ ] 
```
{ "_id": 1,
  "pet": "cat",
  "fur": "soft",
  "claws": "sharp",
  "name": "Furball" }
```

- [ ] 
```
{ "_id": 1,
  "pet": "cat",
  "attributes": { "coat": "soft fur",
                  "paws": "cute but deadly" },
  "name": "Furball" }
```

- [x] **None of the above.**

<br/><br/>


## Quiz: Updating Documents in the shell
### Problem: Given a pets collection where each document has the following structure and fields:
```
{
 "_id": ObjectId("5ec414e5e722bb1f65a25451"),
 "pet": "wolf",
 "domestic?": false,
 "diet": "carnivorous",
 "climate": ["polar", "equatorial", "continental", "mountain"]
}
```
Which of the following commands will add new fields to the updated documents?
Check all answers that apply:

- [x]
```
db.pets.updateMany({ "pet": "cat" },
                   { "$push": { "climate": "continental",
                                "look": "adorable" } })
```

- [x]
```
db.pets.updateMany({ "pet": "cat" },
                   { "$set": { "type": "dangerous",
                               "look": "adorable" }})
```

- [ ]
```
db.pets.updateMany({ "pet": "cat" },
                   {"$set": { "domestic?": true, "diet": "mice" }})
```

- [ ]
```
db.pets.updateMany({ "pet": "cat" },
                   { "$set": { "climate": "continental" }})
```
<br/><br/>


## Quiz 1: Deleting Documents
### Problem: The sample dataset contains a few databases that we will not use in this course. Clean up your Atlas cluster and get rid of all the collections in these databases:
```
sample_analytics
sample_geospatial
sample_weatherdata
```
Does removing all collections in a database also remove the database?

Choose the best answer:
- [x] **yes**
- [ ] no
<br/><br/>


## Quiz 2: Deleting Documents
### Problem: Which of the following commands will delete a collection named villains?
Check all answers that apply:

- [x] **db.villains.drop()**
- [ ] db.villains.delete()
- [ ] db.villains.dropAll()