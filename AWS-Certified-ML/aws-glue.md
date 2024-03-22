# AWS Glue

## AWS Glue Data Catalog

A metadata repo for all of your tables.
- Automated schema inference
- Integrates with Athena/Redshift

The underlying platform is a serverless Apache Spark platform.

### Glue Crawlers

Crawlers parse through your data store to find schemas and partitions.
- They can be ran on schedule or on demand.
- They need an IAM role to access data stores.
- Crawlers extract partitions based on how your data is organized.

## Glue ETL

Extract, Transform & Load (ETL)

Glue ETL allows you transform, clean and enrich your data before you perform any analysis on it.
- Fully managed and you only pay for what you use.
- Can be scheduled or run off a trigger/events

Bundle Transformations:
- DropFields, DropNullFields
- Filter
- Join
- Map

Machine Learning Transformations:
- FindMatches ML

## Glue Data Brew

Glue Data Brew allows you to  clean and normalize data through a GUI, so no code needs to be written.
- There are 250+ prebuilt transformations to help you clean and normalize your tasks.
- Recipes - A list of data cleaning steps.

## AWS Athena

Allows us to query our data instantly in AWS S3.