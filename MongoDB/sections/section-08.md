# MongoDB CRUD: Replace and Delete Documents

[Home](../README.md)

## replaceOne()

To replace documents in MongoDB, we use the replaceOne() method. The replaceOne() method takes the following parameters:

- filter: A query that matches the document to replace.
- replacement: The new document to replace the old one with.
- options: An object that specifies options for the update, not required.

```js
db.collection.replaceOne(filter, replacement, options)

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

## updateOne()

The `updateOne()` method accepts a filter document, an update document, and an optional options object. MongoDB provides update operators and options to help you update documents: `$set`, `$upsert`, and `$push`.

### $set

The `$set` operator replaces the value of a field with the specified value:

```js
db.podcasts.updateOne(
  {
    _id: ObjectId("5e8f8f8f8f8f8f8f8f8f8f8"),
  },

  {
    $set: {
      subscribers: 98562,
    },
  }
)
```

### $upsert

The `$upsert` option creates a new document if no documents match the filtered criteria:

```js
db.podcasts.updateOne(
  { title: "The Developer Hub" },
  { $set: { topics: ["databases", "MongoDB"] } },
  { upsert: true }
)
```

### $push

The `$push` operator adds a new value to the hosts array field:

```js
db.podcasts.updateOne(
  { _id: ObjectId("5e8f8f8f8f8f8f8f8f8f8f8") },
  { $push: { hosts: "Nic Raboy" } }
)
```

## findAndModify()

The findAndModify() method is used to find and replace a single document in MongoDB. It accepts a filter document, a replacement document, and an optional options object.

- Avoids round trips to the server, you can combine a find and modify method.

```js
db.podcasts.findAndModify({
  query: { _id: ObjectId("6261a92dfee1ff300dc80bf1") },
  update: { $inc: { subscribers: 1 } },
  new: true,
})
```

## updateMany()

To update multiple documents, use the `updateMany()` method. This method accepts a filter document, an update document, and an optional options object. The following code shows an example:

```js
db.books.updateMany(
  { publishedDate: { $lt: new Date("2019-01-01") } },
  { $set: { status: "LEGACY" } }
)
```

## Delete Documents in MongoDB

### deleteOne()

Deletes one document that meet the filter option.

```js
db.podcasts.deleteOne({ _id: Objectid("6282c9862acb966e76bbf20a") })
```

### deleteMany()

Deletes multiple documents that meet the filter option.

```js
db.podcasts.deleteMany({category: “crime”})
```

## Proof of Completion

[Click Here](https://ti-user-certificates.s3.amazonaws.com/ae62dcd7-abdc-4e90-a570-83eccba49043/09d120a6-17b5-4e81-940e-cd158dd3e8ee-alexandro-valdez-3159c79b-33e2-4335-a137-15adb2db60b4-certificate.pdf)