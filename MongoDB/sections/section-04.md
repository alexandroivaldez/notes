# MongoDB Data Modeling

[Home](../README.md)

"Data that is accesses together should be stored together." - MongoDB

## Questions to Ask Yourself When Data Modeling

1. What does my application do?

2. What data will I store?

3. How will users access this data?

4. What data will be most valuable to me?

## Types of Data Relationships

### One to One

A relationship where a data entity in one set is connected to exactly one data entity in another set.

```json
{
    "_id": ObjectId("123qwe456asd"),
    "title": "Star Wars: Episode IV - A New Hope",
    "director": "George Lucas",
    "runtime": 121 
}
```

### One to Many

A relationship where a data entity in one set is connected to any number of data entities in another set.

```json
{
    "_id": ObjectId("123qwe456asd"),
    "title": "Star Wars: Episode IV - A New Hope",
    "cast": [
        {"actor": "Mark Hamill", "character": "Luke Skywalker"},
        {"actor": "Harrison Ford", "character": "Han Solo"},
        {"actor": "Carrie Fisher", "character": "Princess Leia Organa"},
    ]
}
```

### Many to Many

A relationship where any  number of data entities in one set are connected to any number of data entities in another set.

Primary Ways to Model Many-to-Many:

#### Embedding

Take related data and insert it into the document.

```json
{
    "_id": ObjectId("123qwe456asd"),
    "title": "Star Wars: Episode IV - A New Hope",
    "cast": [
        {"actor": "Mark Hamill", "character": "Luke Skywalker"},
        {"actor": "Harrison Ford", "character": "Han Solo"},
        {"actor": "Carrie Fisher", "character": "Princess Leia Organa"},
    ]
}
```

#### Referencing

Refer to documents in another collection in our document.

```json
{
    "_id": ObjectId("123qwe456asd"),
    "title": "Star Wars: Episode IV - A New Hope",
    "director": "George Lucas",
    "runtime": 121
    "filming_locations": [
        ObjectId("123qwe456asd"),
        ObjectId("qwe123asd456"),
        ObjectId("poi098ulk098"),
    ]
}
```

## Embedding Data in Documents

**Embedding** - Store related data in a single document.

- Simplify queries and improves overall query performance.
- Ideal for one-to-many and many-to-many relationships among data.

```js
{
    name: 'John Doe',
    age: 30,
    address: {
    street: '123 Main Street',
    city: 'New York',
    country: 'USA'
    },
    contacts: [
        { type: 'email', value: 'john.doe@example.com' },
        { type: 'phone', value: '123-456-7890' }
    ]
}
```

**WARNING:**

- Embedding data into a single document can create large documents.
Large documents have to be read into memory in full, which can result in a slow application performance for your end user.

- Continuously adding data without limit creates **unbounded documents**.
  - Unbounded documents may exceed the BSON document threshold of 16 MB.

## Referencing Data in Documents

**Referencing** - When you save the _id field of one document in another document as a link between the two.

- AKA linking or data normalization.

- PROS:
  - No duplication of data.
  - Smaller documents.

- CONS:
  - Querying from multiple documents cost extra resources and impacts read performance.

```json
// User document
{
  "_id": ObjectId("61f3c6f0ea83987c19f0b723"),
  "name": "John Doe",
  "age": 30,
  "email": "john.doe@example.com"
}

{
  "_id": ObjectId("61f3c6f0ea83987c19f0b724"),
  "title": "Sample Post",
  "content": "This is a sample post content.",
  "user_id": ObjectId("61f3c6f0ea83987c19f0b723") // Reference to the user document
}
```

## Proof of Completion

[Click Here](https://ti-user-certificates.s3.amazonaws.com/ae62dcd7-abdc-4e90-a570-83eccba49043/09d120a6-17b5-4e81-940e-cd158dd3e8ee-alexandro-valdez-8534c382-dd89-43eb-9abd-f4d57aa5d1c6-certificate.pdf)
