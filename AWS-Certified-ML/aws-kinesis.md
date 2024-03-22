# AWS Kinesis

Kinesis is an alternative to Apache Kafka. It's particurly good for **"real-time"** big data. Your data is automatically replicated to 3 availability zones.

Four Kensis Services:

1. [Kinesis Streams](#kinesis-streams)
    - Allows you to create real time ML apps.
2. [Kinesis Firehose](#kinesis-firehose)
    - Allows you to ingest massive data in NEAR real time.
3. [Apache Flink](#apache-flink-kinesis-data-analytics)
    - Allow you to perform real time data analytics on streams.
4. [Kinesis Video Streams](#kinesis-video-streams)
    - Allows you to create ML apps from real time video streams.

The exam will test you on which service y, you should use in scenerio x.

```md
IOT Device/Logs -> Kinesis Streams -> Kinesis Analytics -> Kinesis Firehose -> S3 Bucket
```

## Kinesis Streams

- Data from streams is divided into "shards" or "partitions".

    - `producer -> shards -> consumers`

- Data is held for 24 hours by default, up to 365 days.
- Multiple apps can "consume" the same stream.
- Data cannot be deleted once it is inserted into a stream.
- Records can be UP TO 1mb

### Kinesis Streams Capacity Modes

1. Provisioned Mode

    - You choose the number of shards provisioned.
    - You can scale the shards manually or use an API to scale the shards.
    - Shards get 1mb/s in
    - Shards get 2mb/s out
    - Pricing is per shard provisioned per hour.

2. On-demand Mode

    - Capacity is changed overtime on-demand, therefore you don't need to manage or provision the capacity.
    - Pricing is per stream per hour + data in/out per GB

### Kinesis Streams Limits

- Producers can send 1mb/s at write time per shard.
- Consumers can read 2mb/s per shard, and 5 API calls per second.
- Data is held for 24 hours by default, up to 365 days.

## Kinesis Firehose

Firehose allows you to store data into target destinations.
- Fully managed service
- **Near** real time
- Ingests into S3/Redshift/ElasticSearch/Splunk
- Automatic scaling
- Data conversions
- Data transformations using AWS Lambda
- When the target is S3 you can perform compression (gzip, zip or snappy)
- You pay for the amount of data going through Firehose

### Data Streams VS Firehose

Data streams is for building real time apps and Firehose is for delivering data.

Data streams is custom code, real time, automatic scaling on demand, and has data storage from 1 to 365 days.

Firehouse is fully managed, near real time, automatic scaling by default, but has not data storage.

## Apache Flink (Kinesis Data Analytics)

Service for simple transformations, continous metric generation and responsive analytics.
- Serverless
- You pay only for what you use (not cheap)
- SQL or Flink to write computations
- Lambda for preprocessing data

### Machine Learning on Kinesis Data Analytics

1. RANDOM_CUT_FOREST
2. HOTSPOTS

## Kinesis Video Streams

Streams for... you guessed it, videos.

- The procedures are physical cameras, and you can have one producer per video stream.
    - 1000 cameras == 1000 producers

- The consumers can be built by you, AWS SageMaker or AWS Rekognition.

- You can keep data from the streams from 1 hour to 10 years!!!