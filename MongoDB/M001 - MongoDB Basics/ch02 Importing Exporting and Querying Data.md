# Ch02. Importing, Exporting, and Querying Data

## How does MongoDB store data?
JSON (Viewed)
- JavaScript Standard Object Notation
- Separate key, value with a colon
- Pros
  - Friendly
  - Readable
  - Familiar
- Cons
  - Text-based
    - Text parsing is very Slow
  - Space-consuming
  - Limited number of data types

BSON (Stored)
- Binary JSON
- optimized for
  - Speed
  - Space
  - Flextibility
- High performance
- General-purpose focus

|  | JSON | BSON |
| -- | -- | -- |
| Encoding | UTF-8 String | Binary |
| Data Support | String, Boolean, Number, Array | String, Boolean, Number(Integer, Long, Float, ...), Array, Date, Raw Binary |
| Readability | Human and Machine | Machine only |


JSON vs. BSON
- https://www.mongodb.com/json-and-bson

BSON
- https://bsonspec.org/

## Importing and Exporting Data
### Export
BSON 으로 export 하기
```
mongodump --uri "<Atlas Cluster URI>"
```

JSON 으로 export 하기
```
mongoexport --uri "<Atlas Cluster URI>"
            --collection=<collection name>
            --out=<filename>.json
```

### Import
BSON 파일 import 하기
```
mongostore --uri "<Atlas Cluster URI>"
           --drop dump
```

JSON 파일 import 하기
```
mongoimport --uri <"Atlas Cluster URI>"
            --drop=<filename>.json
```
## Find command
it
- iterates through a cursor

cursor
- a pointer to a result set of a query

pointer
- a direct address of the memory location