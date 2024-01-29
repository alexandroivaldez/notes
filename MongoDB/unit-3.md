# MongoDB Data Modeling Intro

**Data modeling** - the process of defining how data is stored and the process of defining the relationships that exist among different entities in your data.

## Types of Data Relationships

### One to One

- A relationship where a data entity in one set is connected to exactly one data entity in another set.

### One to Many

- A relationship where a data entity in one set is connected to any number of data entities in another set.

### Many to Many

- A relationship where any number of data entities in one set is connected to any number of data entities in another set.

## Ways to Model Relationships

### Embedding

- We take related data and insert it into our document.

```json
{
    "_id": ObjectId("12309ba34bfb840"),
    "title": "Star Wars: Episode IV - A New Hope",
    "cast": [
        {"actor": "Mark Hamill", "character": "Luke Skywalker"},
        {"actor": "Harrison Ford", "character": "Han Solo"},
        {"actor": "Carrie Fisher", "character": "Princess Leia"}
    ]
}
```

#### Embedding Pros

- Avoids application join
- Provides better performance for read operations
- Allows developers to update related data in a single write operation.

#### Embedding Cons

- Embedding data into a single document can create large documents.
- Large documents have to be read into memory in full, which can result in a slow application performance for your end user.
- Continuously adding data without limit creates unbounded documents.
  - Unbounded documents may exceed the BSON document threshold of 16 MB.

### Referencing

- We refer to documents in another collection in our document by using references. We save the _id field of one document in another document as a link between the two.

  - Using references is sometimes called linking or data normalization.

```json
{
    "_id": ObjectId("12309ba34bfb840"),
    "title": "Star Wars: Episode IV - A New Hope",
    "runtime": 121,
    "filming_locations": [
        ObjectId("1239dfb934b0f80"),
        ObjectId("22349f3032ff899")
    ]
}
```

#### Referencing Pros

- No duplication of data
- Smaller documents

#### Referencing Cons

- Querying from multiple documents costs extra resource and impacts read performance.

## Scaling a Data Model

- Avoid documents that are unbounded. This normally happens when you're embedding.

- Avoid more than the document size limit of 16MB.
