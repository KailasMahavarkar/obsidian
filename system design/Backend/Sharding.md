
Sharding is a database architecture technique that involves dividing a large dataset into smaller, more manageable pieces called "shards," which are distributed across multiple servers. Each shard holds a portion of the data, improving performance, scalability, and manageability by spreading the load and enabling parallel processing.

1. **Horizontal Sharding (Range-Based Sharding)** - Data is divided into shards based on a range of values for a particular key. For example, users with IDs 1-1000 go to one shard, and users with IDs 1001-2000 go to another.

2. **Vertical Sharding** - Different types of data are stored in different shards. For example, user profile information is stored in one shard, while transaction data is stored in another.

3. **Hash-Based Sharding** - Data is divided into shards based on the hash value of a key. A hash function is applied to the key, and the result determines the shard where the data will be stored.

4. **Directory-Based Sharding** - A lookup service or directory keeps track of which shard contains which data. When accessing data, the directory is consulted to determine the correct shard.

