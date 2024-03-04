# MongoDB CRUD: Insert and Find Documents

[Home](../README.md)

## Insert

### insertOne()

The insertOne() method inserts one document in the specified collection.

```js
db.collection.insertOne({document})
```

If the collection does not exist, mongoDB will create the collection for you.

### insertMany()

The insertMany() method inserts multiple documents in the specified collection.

```js
db.collection.insertMany([{document1}, {document2}, ...])
```

## Finding

### find()

The code below returns documents from a collection:

```js
db.collection.find()
```

## $eq

The $eq operator allows you to find documents who's field values EQual the specified valued.

> { field: {$eq: `<value>` }}

> { field: `<value>` }

The code below the corresponding document who's state fields value is "AZ":

```js
db.collection.find({state: "AZ"})
```

### $in

The $in operator allows us to select all documents that have a field value equal  to any of the values specified in the array.

Basic Syntax:

```js
db.collection.find({
    <field>: { $in:
    [<value>, <value> , ...]
    }
})
```

Find every document with a city value of either Phoenix or Chicago:

```js
db.zips.find({ city: { $in: ["Phoenix", "Chicago"]}})
```

### Comparison Operators

```js
<field>: { <operator> : <value> }
```

$gt - Returns documents where the field contains a value greater than the specified value.

Find documents in sales, who's price is > 50:

`db.sales.find({ "items.price" : {$gt: 50}})`

$lt - Returns documents where the field contains a value less than the specified value.

Find documents in sales, who's price is < 50:

`db.sales.find({ "items.price" : {$lt: 50}})`

$lte - Returns documents where the field contains a value greater than or equal to the specified value.

Find documents in sales, who's price is >= 50:

`db.sales.find({ "items.price" : {$gte: 50}})`

$gte - Returns documents where the field contains a value less than or equal to the specified value.

Find documents in sales, who's price is <= 50:

`db.sales.find({ "items.price" : {$lte: 50}})`

## Querying

### $elemMatch

Allows you to find subdocuments that match specific criteria in an array.

```js
db.sales.find({
  items: {
    $elemMatch: { name: "laptop", price: { $gt: 800 }, quantity: { $gte: 1 } },
  },
})
```

### Logical Operators

Use implicit $and to select documents that match multiple expressions. For example:

```js
db.routes.find({ "airline.name": "Southwest Airlines", stops: { $gte: 1 } })
```

Use the $or operator to select documents that match at least one of the included expressions. For example:

```js
db.routes.find({
  $or: [{ dst_airport: "SEA" }, { src_airport: "SEA" }],
})
```

Use the $and operator to use multiple $or expressions in your query.

```js
db.routes.find({
  $and: [
    { $or: [{ dst_airport: "SEA" }, { src_airport: "SEA" }] },
    { $or: [{ "airline.name": "American Airlines" }, { airplane: 320 }] },
  ]
})
```

## Proof of Completion

[Click Here](https://ti-user-certificates.s3.amazonaws.com/ae62dcd7-abdc-4e90-a570-83eccba49043/09d120a6-17b5-4e81-940e-cd158dd3e8ee-alexandro-valdez-f82796fc-3025-46b2-bd12-941912c753f4-certificate.pdf)