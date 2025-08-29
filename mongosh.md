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
## 28. To retrieve documents which contains the feild, including documents share the feild value is null. if it set false then query return only documents that do not contain the feild 

```bash
db.collection_name.find({ attribute: { $exists : <boolean> } })

```
## 29. To retrieve the documents where the feild value matches the specified regular expression pattern, and here options denotes various flags 

```bash
db.collection_name.find({attribute :{ $regex: /pattern/, $options: '<options>' }})
```
# Updation Operation

## 30. To update single document matching a condition 

```bash
db.collection_name.updateOne({attribute : "value"}, {$set : {attribute : "newValue" }})
                  or
db.collection_name.updateOne({attribute : "value"}, {$set : {attribute : "newValue" }},{upsert : true})
```
## 31. To update multiple documents matching a condition

```bash
db.collection_name.updateMany({attribute : "value"}, {$set : {attribute : "newValue" }})
                  or
db.collection_name.updateMany({attribute : "value"}, {$set : {attribute : "newValue" }},{upsert : true})
```

## 32. To increment a field in documents matching a condition

```bash
db.collection_name.updateOne/updateMany({attribute : "value"}, {$inc : {numericFeild : <number>  }})
```
## 33. To multiply a field in documents matching a condition

```bash
db.collection_name.updateOne/updateMany({attribute : "value"}, {$mul : {numericFeild : <number>  }})
```
## 34. To rename a field/fields in documents matching a condition

```bash
db.collection_name.updateOne/updateMany({attribute : "value"}, { $rename: { <oldFieldName>: <newFieldName>, ... } }})
```
## 35. To set the value of field/fields  in documents matching a condition

```bash
db.collection_name.updateOne/updateMany({attribute : "value"}, { $set: { <field1>: <value1>, <field2>: <value2>, ... } })
```
## 36. To remove a field/fields  in documents matching a condition

```bash
db.collection_name.updateOne/updateMany({attribute : "value"}, { $unset: { <field1>: "", <field2>: "", ... } })
```
# Deletion Operation

## 37. To delete a first (single) document matching a condition

```bash
db.collection_name.deleteOne({ attribute: "value" })
```
## 38. To delete a multiple document matching a condition

```bash
db.collection_name.deleteMany({ attribute: "value" })
```

# Single Purpose Aggregation 

## 39. To count the number of documents matching a condition

```bash
db.collection_name.count({ attribute: "value" })
```
## 40. To get arary of distinct values of a field matching a condition

```bash
db.collection_name.distinct("<field_name>", { attribute: "value" })
```

# Aggregation Pipeline Operators

## 41. To include or exclude specific fields from the documents

The `$project` stage is used in an aggregation pipeline to **reshape documents** by including, excluding, or adding new computed fields.

```bash
db.collection_name.aggregate([
  {
    $project: {
      field1: 1,   # include
      field2: 1,   # include
      field3: 0    # exclude
    }
  }
])
```
## 42. To group documents by a specified field and perform aggregations

The `$group` stage is used in an aggregation pipeline to **group documents** by an expression and apply accumulator operations like `$sum`, `$avg`, `$max`, `$min`, `$push`, etc.

```bash
db.collection_name.aggregate([
  {
    $group: {
      _id: "$<field>",      # group by this field
      totalCount: { $sum: 1 },
      averageValue: { $avg: "$<numeric_field>" }
    }
  }
])
```

## 43. To filter documents in the aggregation pipeline

The `$match` stage is used in an aggregation pipeline to **filter documents** based on a given condition (similar to `find()` query filter).

```bash
db.collection_name.aggregate([
  {
    $match: {
      <field>: <value>
    }
  }
])
```

## 44. To sort documents in the aggregation pipeline

The `$sort` stage is used in an aggregation pipeline to **order documents** by one or more fields, in ascending (`1`) or descending (`-1`) order.

```bash
db.collection_name.aggregate([
  {
    $sort: {
      <field1>: 1,   # ascending
      <field2>: -1   # descending
    }
  }
])
```
## 45. To limit the number of documents in the aggregation pipeline

The `$limit` stage is used in an aggregation pipeline to **restrict the number of documents** passed to the next stage.

```bash
db.collection_name.aggregate([
  {
    $limit: <number>
  }
])
```

## 46. To write the aggregation results to a collection

The `$out` stage is used in an aggregation pipeline to **write the output documents** to a specified collection.  
⚠️ It replaces the entire target collection with the new results.

```bash
db.collection_name.aggregate([
  {
    $out: "<target_collection>"
  }
])
```

## 47. To skip a specified number of documents in the aggregation pipeline

The `$skip` stage is used in an aggregation pipeline to **bypass a given number of documents** before passing the rest to the next stage.

```bash
db.collection_name.aggregate([
  {
    $skip: <number>
  }
])
```
## 48. To count the number of documents in the aggregation pipeline

The `$count` stage is used in an aggregation pipeline to **return the number of documents** that pass through the pipeline.

```bash
db.collection_name.aggregate([
  {
    $count: "<fieldName>"
  }
])
```
## 49. To deconstruct an array field into multiple documents

The `$unwind` stage is used in an aggregation pipeline to **split array elements** into separate documents, creating one document per array element.

```bash
db.collection_name.aggregate([
  {
    $unwind: "$<arrayField>"
  }
])
```
## 50. To get the minimum value of a field

The `$min` accumulator is used in an aggregation pipeline (usually with `$group`) to **return the smallest value** for a given field.

```bash
db.collection_name.aggregate([
  {
    $group: {
      _id: "$<groupField>",
      minValue: { $min: "$<numericField>" }
    }
  }
])
```

## 50. To get the maximum value of a field

The `$max` accumulator is used in an aggregation pipeline (usually with `$group`) to **return the largest value** for a given field.

```bash
db.collection_name.aggregate([
  {
    $group: {
      _id: "$<groupField>",
      maxValue: { $max: "$<numericField>" }
    }
  }
])
```

## 52. To query documents from a collection

The `find()` method is used to **retrieve documents** from a collection based on a filter condition.

```bash
db.collection_name.find({ <field>: <value> })
```

## 53. To skip documents when querying

The `skip()` method is used with `find()` to **bypass a specified number of documents** in the query result.

```bash
db.collection_name.find().skip(<number>)
```

## 54. To limit the number of documents when querying

The `limit()` method is used with `find()` to **restrict the number of documents** returned.

```bash
db.collection_name.find().limit(<number>)
```





