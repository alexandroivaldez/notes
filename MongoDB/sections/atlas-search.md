# MongoDB Atlas Search

Atlas Search allows you to create a search experience for your users without having to write a search algorithm.

Relevance-based Search - A type of searching that searches based on relevance not on exact matches.

Search indexes - NOT the same as database indexes. Search indexes specify how records are referenced for relevance-based search.

Apache Lucene - open source analyzer used in Atlas Search

## Creating a Search Index with Dynamic Mapping

All fields are indexed EXCEPT booleans, objectIds and timestamps.

Dynamic mapping automatically indexes common data types in a collection.

MongoDB automatically generates the search index for you.


Search Index Example:

```js
{
    "name": "sample_supplies-sales-dynamic",
    "searchAnalyzer": "lucene.standard",
    "analyzer": "lucene.standard",
    "collectionName": "sales",
    "database": "sample_supplies",
    "mappings": {
        "dynamic": true
    }
}
```

Create the Atlas Search index:

```md
atlas clusters search indexes create --clusterName myAtlasClusterEDU -f /app/search_index.json
```