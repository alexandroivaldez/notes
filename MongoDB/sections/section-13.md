# MongoDB Indexes

[Home](../README.md)

## Indexes

Special data structures that store a small portion of the data.

- Ordered and easy to search efficiently.
- Point to the document identity.
- Faster and helps save $.

## Creating a Single Field Index

Review the code below, which demonstrates how to create a single field index in a collection.

### Create a Single Field Index

Use `createIndex()`` to create a new index in a collection. Within the parentheses of createIndex(), include an object that contains the field and sort order.

```js
db.customers.createIndex({
  birthdate: 1
})
```

### Create a Unique Single Field Index

Add {unique:true} as a second, optional, parameter in createIndex() to force uniqueness in the index field values. Once the unique index is created, any inserts or updates including duplicated values in the collection for the index field/s will fail.

```js
db.customers.createIndex({
  email: 1
},
{
  unique:true
})
```

MongoDB only creates the unique index if there is no duplication in the field values for the index field/s.

View the Indexes used in a Collection
Use getIndexes() to see all the indexes created in a collection.

`db.customers.getIndexes()`

Check if an index is being used on a query
Use explain() in a collection when running a query to see the Execution plan. This plan provides the details of the execution stages (IXSCAN , COLLSCAN, FETCH, SORT, etc.).

The IXSCAN stage indicates the query is using an index and what index is being selected.
The COLLSCAN stage indicates a collection scan is perform, not using any indexes.
The FETCH stage indicates documents are being read from the collection.
The SORT stage indicates documents are being sorted in memory.

```js
db.customers.explain().find({
  birthdate: {
    $gt:ISODate("1995-08-01")
    }
  })
db.customers.explain().find({
  birthdate: {
    $gt:ISODate("1995-08-01")
    }
  }).sort({
    email:1
    })
```
