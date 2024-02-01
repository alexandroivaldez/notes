# Connecting to a MongoDB Database

## Using MongoDB Connection Strings

**Connection Strings** - Allow you to connect to a mongoDB cluster, you can connect using shell, compass or another application.

**Standard Format** - Used to connect to standalone clusters,replica sets or sharded clusters.

**DNS Seed List Format** - Provides a DNS server list to the connection string.

- Gives more flexibility of deployment.
- Ability to change servers in rotation without reconfiguring clients.

**Getting your Connection String** - Database > Cluster > Connect > Select your Connection Method > Receive connection string.

## Connection String Breakdown

- **mongodb://** - is the required prefix that identifies this as a standard connection string.
- **username:password@** - the credentials that the client attempts to authenticate with. If no credentials are given, MongoDB will attempt to authenticate with the admin user.
- **host[:port]** - this is where the database instance is running.
- **?< options >** - This is where we can specify specific connection options.

## Connecting to a MongoDB Atlas Cluster with the Shell

```shell
mongosh "connectionString" --apiVersion 1 --username admind
Enter password: ********
```

The shell is a Node.js REPL environment so you can write JavaScript expressions.

## Connecting to a MongoDB Atlas Cluster with Compass

MongoDB Compass is a GUI, that allows us to query and analyze our data, and compose aggregation pipelines.

## Connecting to a MongoDB Atlas Cluster from an Application

**MongoDB Drivers** - Connects MongoDB to applications via programming languages

**mongodb.com/docs/drivers** - Shows a list of all the available drivers for a plethora of languages.
