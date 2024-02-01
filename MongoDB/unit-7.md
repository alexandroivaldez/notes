# MongoDB CRUD Operations: Replace and Delete Documents

## replaceOne()

The replaceOne() method in MongoDB is used to replace a single document in a collection with a new document.

```js
// Template
db.collection.replaceOne(filter, replacement, options)

// Example: Replace missing information inside of the specified document
db.books.replaceOne(
  {
    _id: ObjectId("6282afeb441a74a98dbbec4e"),
  },
  {
    title: "Data Science Fundamentals for Python and MongoDB",
    isbn: "1484235967",
    publishedDate: new Date("2018-5-10"),
    thumbnailUrl:
      "https://m.media-amazon.com/images/I/71opmUBc2wL._AC_UY218_.jpg",
    authors: ["David Paper"],
    categories: ["Data Science"],
  }
)
```

**filter** - A document that specifies the criteria for the document to be replaced. It works similar to the find() method and identifies the document to be replaced.

**replacement** - A document that contains the new data you want to replace the existing document with. This document should have the same _id value as the document you want to replace if you want to retain the same _id.

**options (optional)** -  An optional document that can contain additional options for the operation, such as upsert (default is false) to insert the replacement document if no matching document is found.

### Example

Suppose you have a collection called "users" with the following documents:

```js
{
  _id: 1,
  name: "John",
  age: 30
}
```

You can use replaceOne() to update John's age to 35:

```js
db.users.replaceOne(
   { _id: 1 },
   { name: "John", age: 35 }
)
```

If you want to **upsert** (insert if not found) a document with _id: 2 if it doesn't already exist, you can use the upsert option:

```js
db.users.replaceOne(
   { _id: 2 },
   { name: "Jane", age: 25 },
   { upsert: true }
)
```

## updateOne()

The updateOne() method in MongoDB is used to update a single document in a collection based on a specified filter.

```js
db.collection.updateOne(filter, update, options)
```

- **filter**: A document that specifies the criteria for the document to be updated. It works similar to the find() method and identifies the document to be updated.

- **update**: A document that contains the modifications you want to make to the selected document. It uses update operators like $set, $inc, $push, etc. to specify the changes you want to apply.

- **options (optional)**: An optional document that can contain additional options for the operation, such as upsert (default is false) to insert the document if no matching document is found, and bypassDocumentValidation (default is false) to skip document validation.

### $set

The $set operator replaces the value of a field with the specified value. Suppose you have a collection called "users" with the following document:

```js
{
  _id: 1,
  name: "John",
  age: 30
}
```

You can use updateOne() to update John's age to 35:

```js
db.users.updateOne(
   { _id: 1 },
   { $set: { age: 35 } }
)
```

If you want to upsert (insert if not found) a document with _id: 2 and name "Jane" and age 25 if it doesn't already exist, you can use the upsert option:

```js
db.users.updateOne(
   { _id: 2 },
   { $set: { name: "Jane", age: 25 } },
   { upsert: true }
)
```

### $upsert

The upsert option creates a new document if no documents match the filtered criteria. Here's an example:

```js
db.podcasts.updateOne(
  { title: "The Developer Hub" },
  { $set: { topics: ["databases", "MongoDB"] } },
  { upsert: true }
)
```

### $push

The $push operator adds a new value to the hosts array field. Here's an example:

```js
db.podcasts.updateOne(
  { _id: ObjectId("5e8f8f8f8f8f8f8f8f8f8f8") },
  { $push: { hosts: "Nic Raboy" } }
)
```

## findAndModify()

The findAndModify() method is used to find and replace a single document in MongoDB. It accepts a filter document, a replacement document, and an optional options object. The following code shows an example:

```js
db.podcasts.findAndModify({
  query: { _id: ObjectId("6261a92dfee1ff300dc80bf1") },
  update: { $inc: { subscribers: 1 } },
  new: true,
})
```

## updateMany()

To update multiple documents, use the updateMany() method. This method accepts a filter document, an update document, and an optional options object. The following code shows an example:

```js
db.books.updateMany(
  { publishedDate: { $lt: new Date("2019-01-01") } },
  { $set: { status: "LEGACY" } }
)
```

## Deleting Documents in MongoDB

To delete documents, use the deleteOne() or deleteMany() methods. Both methods accept a filter document and an options object.

### Delete One Document

The following code shows an example of the deleteOne() method:

```js
db.podcasts.deleteOne({ _id: Objectid("6282c9862acb966e76bbf20a") })
```

### Delete Many Documents

The following code shows an example of the deleteMany() method:

```js
db.podcasts.deleteMany({category: “crime”})
```

- Code will delete every document in the "podcasts" collection where the "category" field is equal to "crime." It will remove all the documents that match the specified filter, not just the "category" field.
