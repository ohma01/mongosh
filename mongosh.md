# MongoSh Commands Cheat Sheet

# DataBase Creation And Collection
## 1. Create / Switch Database
```bash
use databaseName
```

## 2. To create collection
```bash
db.createCollection('collection_name')
```
## 3. To show database

```bash
show dbs
```
## 4. To show collections

```bash
show collections
```
##  5. To drop collection

```bash
db.collection_name.drop()
```
## 6. To drop Database

```bash
db.dropDatabase()
```
# Insertion Operation

## 7. To inserting one document at a time 

```bash
db.collection_name.insertOne({document})
```
## 8. To insert many documents at a same time

```bash
db.collection_name.insertMany([{document1},{document2},...])
```

# Retrieval Operation

## 9. To retrieve one document

```bash
db.collection_name.findOne()
```
## 10. To retrieve all documents

```bash
db.collection_name.find()
      or
db.collection_name.find({query},{projection})
```

## 11. To format output received by find()

```bash
db.collection_name.find().pretty()
```

## 12. To retrieve document from embedded document 

```bash
db.collection_name.find({"attribute1.attribute2" : "value"},{projection})
```

## 13. To retrieve documents based on AND logical operator

```bash
db.collection_name.find({ $and: [ {attributel : "value1"}, {attribute2 : "value2"} ]})
```
## 14. To retrieve documents based on OR logical operator

```bash
db.collection_name.find({ $or: [ {attributel : "value1"}, {attribute2 : "value2"} ]})
```

## 15. To retrieve documents based on NOR logical operator

```bash
db.collection_name.find({ $nor: [ {attributel : "value1"}, {attribute2 : "value2"} ]})
```

## 16. To retrieve documents based on NOT logical operator

```bash
db.collection_name.find({ $not: {"expression"}})
```

## 17. To retrieve documents where the value of feild is not equal to the specified value 

```bash
db.collection_name.find({ attribute: {$ne: "value" }})
```

## 18. To retrieve documents where the value of feild that is equal to the specified value

```bash
db.collection_name.find({ attribute: {$eq: "valuel" }})
```
## 19. To retrieve documents where the value of feild that is less than the specified value 

```bash
db.collection_name.find({ attribute: {$lt: "value" }})
```
## 20. To retrieve documents where the value of feild that is greater than the specified value

```bash
db.collection_name.find({ attribute: {$gt: "value" }})
```
## 21. To retrieve documents where the value of feild that is less than or equal to the specified value

```bash
db.collection_name.find({ attribute: {$lte: "value" }})
```
## 22. To retrieve documents where the value of feild that is greater than or equal to the specified value

```bash
db.collection_name.find({ attribute: {$gte: "value" }})
```
## 23. To retrieve documents where the value of feild is the values specified in an array 

```bash
db.collection_name.find({ attribute: {$in: ["valuel", "value2",...] }})
```
## 24. To retrieve documents where the value of feild excludes the values specified in an array 

```bash
db.collection_name.find({ attribute: {$nin: ["valuel", "value2",...] }})
```
## 25. To retrieve documents where the value of feild includes the all values specified in an array 

```bash
db.collection_name.find({ attribute: {$all: ["valuel", "value2",...] }})
```

## 26. To retrieve documents where the feild has the exact size of value's array as specified in an number

```bash
db.collection_name.find({ attribute: { $size: number }})
```
## 27. To retrieve documents where the array feild contains at least one element that matches the specified query condition 

```bash
db.collection name.find({ attribute: {$elemMatch : {<query1>, <query2>,... } }})
```
## 28. To retrieve documents which contains the feild, including documents shere the feild value is null. if it set false then query return only documents that do not contain the feild 

```bash
db.collection_name.find({ attribute: { $exists : <boolean> } })

```
## 29. To retrieve the documents where the feild value matches the specified regular expression pattern, and here options denotes various flags 

```bash
db.collection_name.find({attribute :{ $regex: /pattern/, $options: '<options>' }})
```

