# MongoDB CRUD Operations: Insert and Find Documents

## Inserting Documents in a MongoDB Collection

### .insertOne()

Inserts a single document into a collection

```js
db.<collection>.insertOne({document})
```

.insertMany()

### .insertMany()

Inserts multiple documents into a collection

```js
db.<collection>.insertMany([{document},{document}, ...])
```

## Finding Documents in a MongoDB Collection

### $eq

Find documents in a collection who's field match a specific criteria.

Normal syntax:

```js
{ field: {$eq: <value>} }
```

Implicit syntax:

```js
// Template
db.<collection>.find({field: value})

// Example: Finds the document with the corresponding _id
db.zips.find({ _id: ObjectId("5c8eccc1caa187d17ca6ed16") })
```

### $in

Find documents that have a field value equal to any of the values specified in the array.

```js
// Template
db.<collection>.find({
    <field>: {$in:
        [<value>, <value>, ...]
    }
})

// Example: Finds the documents that have city: "PHOENIX" or city: "CHICAGO"
db.zips.find({ city: { $in: ["PHOENIX", "CHICAGO"] } })
```

## Finding Documents by Using Comparison Operators

### $gt

Use the $gt operator to match documents with a field greater than the given value.

```js
db.sales.find({ "items.price": { $gt: 50}})
```

### $lt

Use the $lt operator to match documents with a field less than the given value. 

```js
db.sales.find({ "items.price": { $lt: 50}})
```

### $lte

Use the $lte operator to match documents with a field less than or equal to the given value.

```js
db.sales.find({ "customer.age": { $lte: 65}})
```

### $gte

Use the $gte operator to match documents with a field greater than or equal to the given value.

```js
db.sales.find({ "customer.age": { $gte: 65}})
```

### $elemMatch

Use the $elemMatch operator to find all documents that contain the specified sub document.

```js
db.sales.find({
  items: {
    $elemMatch: { name: "laptop", price: { $gt: 800 }, quantity: { $gte: 1 } },
  },
})
```

## Finding Documents by Using Logical Operators

Use implicit $and to select documents that match multiple expressions.

```js
db.routes.find({ "airline.name": "Southwest Airlines", stops: { $gte: 1 } })
```

### $or

Use the $or operator to select documents that match at least one of the included expressions.

```js
db.routes.find({
  $or: [{ dst_airport: "SEA" }, { src_airport: "SEA" }],
})
```

### $and

Use the $and operator to use multiple $or expressions in your query.

```js
db.routes.find({
  $and: [
    { $or: [{ dst_airport: "SEA" }, { src_airport: "SEA" }] },
    { $or: [{ "airline.name": "American Airlines" }, { airplane: 320 }] },
  ]
})
```
