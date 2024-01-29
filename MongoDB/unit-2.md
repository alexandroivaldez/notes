# Unit 02: Overview of MongoDB and the Document Model

**Documents** - the basic unit of storage in mongoDB. Equivalent to a row in a relational database.

**Collection** - a grouping of documents.

**Database** -  a container for your collections.

## MongoDB Document Model

MongoDB display documents using JSON.

```json
// Example 1
{
"key": value,
"key": value,
"key" : value
}

//Example 2
{
"_id": 1,
"name": "AC3 Phone",
"colors" : ["black", "silver"],
"price" : 200,
"available" : true
}
```

MongoDB stores data using binary JSON also known as **BSON**.

- BSON adds additional data types that are not available in JSON.

**ObjectID** - A data type used to create unique identifiers for the required _id field.

- MongoDB can automatically generate this value for objects that do not have a _id already set.

**Flexible Schema Model** - documents in the same collection are not required to share a common structure of fields and value types by default.
