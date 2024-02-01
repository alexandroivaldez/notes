# Identifying Database Workloads

## IDENTIFYING AND QUANTIFYING ENTITIES

**Entities** - an "entity" typically refers to a document. Each document represents a distinct piece of data and is stored in a collection, which is similar to a table in a relational database.

- A document is a unit of data in MongoDB and is equivalent to a row in a relational database table.

**Attributes** - are the fields or properties within a document. Each attribute represents a specific piece of data within a document. Attributes can hold various types of data, such as strings, numbers, arrays, embedded documents, and more.

## IDENTIFYING READS AND WRITES

### Read Operations

| Entities | Operations | Info Needed | Type |
|----------|----------|----------|----------|
| Books* | Fetch book details | Book details + rating | Read |
| Reviews | Fetch 10 reviews for a book | Reviews + reviewer rating | Read |
| Users | Fetch user details | User details | Read |
| Authors, Books* | Fetch an autor and their books | Book titles + author details | Read |
| Printed Books | Fetch printed book titles where the stock level has fallen below 50 | Book details + stock level | Read |

### Write Operations

| Entities | Operations | Info Needed | Type |
|----------|----------|----------|----------|
| Books* | Add / Update Book | Book details + stock level | Write |
| Printed Books | Sell copy of printed book | Stock level | Write |
| Users | Add/update user | User details | Write |
| Reviews | Add review | Review + book rating | Write |

## QUANTIFYING READS AND WRITES

Estimate the rate of each operation. How many times will each operation be used and at what interval?

- 1000/sec, 2/day, 10/hour, etc...

Then figure out what has the highest rate and design your schema to optimize the workload.