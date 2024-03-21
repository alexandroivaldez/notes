# Amazon S3

[Back](data-engineering.md)

Amazon S3 allows people to store files (objects) such as pdfs, scripts, or generally most files in general, inside of directories (buckets).

Bucket Features:
- Globally unique name
- Objects have a key:
  - `<s3_bucket>/my_object.txt`
- Max object size is 5TB

S3 Data Partitioning

Data partitioning allows you to increase the speed of querying your database by breaking things down into folders.
- Some services even handle partitioning for you.

AWS S3 Durability and Availability

S3 has high durability (99.999999999%), durability meaning that it won't lose an object.

Availability measures how readily available a service is.
- The availability varies depending on the S3 storage class.

## AWS S3 Storage Classes

You must know these for the exam. Also, you can move your objects between classes manually or they will move using an S3 lifecycle config. Here are the classes

### S3 Standard - General Purpose

- 99.99% availability
- Used for frequently accessed data
- Low latency & high throughput
- Can sustain 2 concurrent facility failures

### S3 Infrequent Access

- Designed for data that is less frequently accessed, but also required rapid access when needed.
- It's cheaper than S3 standard

There are two types of infrequent access:

1. Standard-IA
  - 99.9% availability
  - Great for backups or disaster recovery. 
2. One Zone-IA
  - 99.999999999% availability in a SINGLE AZ; the data is lost if the AZ is destroyed (somehow)
  - Good for backup backups of on-premise data, or data that you can recreate since there's a chance that it may be lost if the AZ is destroyed.

## S3 Glacier Storage Classes

Lowcost storage meant for archiving and backup. The price is based on the price for storage and the object retrieval cost.

### Glacier Instant Retrieval

- Despite being a glacier storage class, instant retrieval offers a millisecond retrieval time.
  - Good for data that is accessed very infrequently, but you need it fast when you do need to access it.

### Glacier Flexible Rerieval

Requires minimum storage duration of 90 days.

1. **Expedited** - (1 to 5 minutes)
2. **Standard** - (3 to 5 hours)
3. **Bulk** - (5 to 12 hours)

### Glacier Deep Archive

Requires minimum storage duration of 180 days. Good for long term storage. Very slow retrieval speeds:

1. Standard - (12 hours)
2. Bulk - (48 hours)

## S3 Intelligent-Tiering

Moves objects between different tiers based on usage patterns. There is a small monthly monitoring and auto-tiering fee. *There are no retrieval charges.*

### The different types of S3 Intelligent Tiering:
- Frequent Access Tier - default tier
- Infrequent Access Tier - objects not accessed for 30 days
- Archive Instant Access Tier - objects not accessed for 90 days
- Archive Access Tier (optional) - 90 - 700+ days
- Deep Archive Access Tier - 180 - 700+ days

## Lifecycle Rules

**Transition Actions** - Enable objects to move from one storage class to another.

**Expiration Actions** -  Configure objects to expire after a set time.

![Lifecycle Rule Actions](<images/Screenshot 2024-03-21 at 9.59.30 AM.png>)

## S3 Analytics

Gives you a CSV report that has recommenmdations on when to transition objects to the right storage class. The reccomendations are *only* for S3 Standard and Standard IA.

## S3 Security

There are 3 types of security for Amazon S3 buckets:

1. User-Based
    - IAM policies

2. Resourced-Based
    - Bucket policies
    - Object Access Control list
    - Bucket Access Control List

3. Encryption
    - Objects are encrypted in S3 using encryption keys

## S3 Bucket Policies

Bucket policies are JSON documents:

![Bucket Policy Example](<images/Screenshot 2024-03-21 at 10.12.35 AM.png>)

These policies grant public access to the bucket the policy is on. They also force objects to be encrypted when they are uploaded

## S3 Encryption

Server Side Encryption == SSE

1. SSE-S3 (S3 Managed Keys)
2. SSE-KMS (AWS Key Management Service)
3. SSE-C (Customer Provided Keys)
4. Client Side Encryption

### SSE-S3 (S3 Managed Keys)

- Encryption is handled by AWS S3 managed keys.
- The encryption type is **AES-256**.
- Enabled by default for new objects and new buckets.
- Header: "AES256"

### SSE-KMS (AWS Key Management Service)

- Encryption using keys handled and managed by AWS KMS.
- You can audit key usage using AWS CloudTrail
- Header: "aws:kms"
- You might be impacted by the KMS API limits. This is not good if you have a very high throughput (lost of usage).

### SSE-C (Customer Provided Keys)

- Keys are fully managed by customer outside of AWS.
- HTTPS is used to send key over. MUST be used, you can't use HTTP for obvious reasons.
- AWS does not store the encryption keys the customer provides.

### Client Side Encryption

- Client encrypts the data themselves BEFORE sending it over. Decryption is also handled by the client outside of AWS.

## S3 VPC Endpoints

S3 live in the AWS cloud and are accessible through the public internet. You filter accessibility using bucket policies.

You can use a VPC endpoint gateway so that your connection is private and not through the public internet. Your bucket policy must reflect which VPC endpoints can be used.