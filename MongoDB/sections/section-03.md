# MongoDB and the Document Model

[Home](../README.md)

MongoDB is a **General Purpose Document** database.

## Documents

Basic unit of data in MongoDB. They are similar to JSON objects.

Example MongoDB Document:

```json
{
   "_id": ObjectId("61761a890937b4b8267e6e26"),
   "name": "John Doe",
   "age": 30,
   "email": "johndoe@example.com",
   "address": {
       "street": "123 Main St",
       "city": "Anytown",
       "state": "NY",
       "zip": "12345"
   },
   "interests": ["hiking", "reading", "cooking"]
}
```

### Data Types

Documents are displayed in JSON, but stored in BSON.

**BSON** - Binary JSON, is an extension of JSON that provides additional features and additional data types.

### _id Field

Every document requires an _id field which acts as a primary key. If an inserted document does not include the _id field, MongoDB will automatically generate an ObjectID for the _id field.

## Flexible Schema Model

**Collection** - A grouping of documents.

**Database** - A container for collections.

Documents in a collection do not have to have the same structure, meaning documents may contain different fields. These fields may contain different types.

The example below shows 2 documents that look similar but they have different fields. This showcases MongoDB's flexible schema model:

```json
{
   "_id": ObjectId("61761a890937b4b8267e6e27"),
   "title": "Introduction to MongoDB",
   "author": "Jane Smith",
   "content": "MongoDB is a NoSQL database...",
   "tags": ["MongoDB", "NoSQL", "Database"],
   "published": true,
   "views": 1500
},
{
   "_id": ObjectId("61761a890937b4b8267e6e28"),
   "title": "New Features in MongoDB 5.0",
   "author": "John Doe",
   "content": "MongoDB 5.0 introduces...",
   "tags": ["MongoDB", "NoSQL", "Database", "Updates"],
   "published": false,
   "comments": [
       {
           "user": "Alice",
           "comment": "Excited to try out the new features!"
       },
       {
           "user": "Bob",
           "comment": "Looking forward to it!"
       }
   ]
}
```

## Atlas Data Explorer

A built in tool to interact and manage data from Atlas UI.


## Proof of Completion

[Click Here](https://ti-user-certificates.s3.amazonaws.com/ae62dcd7-abdc-4e90-a570-83eccba49043/09d120a6-17b5-4e81-940e-cd158dd3e8ee-alexandro-valdez-eb4c9d10-bddf-4f59-aa27-5ecbde7389b0-certificate.pdf)