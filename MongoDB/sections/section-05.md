# Connecting to a MongoDB Database

[Home](../README.md)

## Using MongoDB Connection Strings

**Connection strings** - Allows you to connect to your cluster and work with your data.

> mongodb+srv://<>:<>@clusterName.usqsf.mongodb.net/?retryWrites=true@w=majority

### Types of Connection Strings

**Standard Format** - Connect to standalone clusters, replica sets or sharded clusters.

**DNS Seed List Format** - Provides DNS server list to connection string.


The command below returns the connection st ring and stores it in an environment variable.

```shell
MY_ATLAS_CONNECTION_STRING=$(atlas clusters connectionStrings describe myAtlasClusterEDU | sed "1 d")
mongosh -u myAtlasDBUser -p myatlas-001 $MY_ATLAS_CONNECTION_STRING
```

## Proof of Completion

[Click Here](https://ti-user-certificates.s3.amazonaws.com/ae62dcd7-abdc-4e90-a570-83eccba49043/09d120a6-17b5-4e81-940e-cd158dd3e8ee-alexandro-valdez-31476cde-9423-4e1d-9c34-53fb8001d8ec-certificate.pdf)