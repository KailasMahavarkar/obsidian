**You want to add cache server to reduce the load on the database and serve the data faster. Given a set of nodes forming a cluster of cache servers, how do you identify where is the data for a particular key?**

## Hashing
identify the node on which the data resides for the particular key. You can take the hash of the key and modulo the number of servers `hash(key) % (no of servers)`to distribute the keys. This approach is called the **Hash Partitioning** algorithm.

![](https://i.imgur.com/J2uxlQx.png)

**What happens when a node crashes?** Say server ‘C’ crashes. The keys that were mapped to server C now needs to be distributed to the remaining servers. _What happens to the keys that were mapped to servers ‘A’ and ‘B’?_ They will also be remapped. Why? Remember the routing algorithm? We take the hash of the key and mod the number of servers. Now the number of servers has changed from 3 to 2.

## Consistent Hashing

Consistent Hashing is a distributed hashing algorithm that is independent of the number of servers. It maps the servers and the keys to a hash ring. There are infinite number of points on the ring where the keys can be mapped now.

![](https://i.imgur.com/tvvDZyj.png)

**What happens when you add new cache servers?** Let’s say we add one server ‘D’ and it gets mapped in between the servers ‘A’ and ‘B’ in the ring. Only the keys which fall in between the servers ‘A’ and ‘D’ will be remapped to server ‘D’ and all the remaining keys will be untouched.

![](https://i.imgur.com/NLRnL9o.png)

> Practically, data is not distributed uniformly , rather it’s randomly distributed.

![](https://i.imgur.com/2OpjXxt.png)

So, randomized data can lead to problem of **hotspots**

**How to avoid hotspots?**  
Instead of mapping a server to one position in the ring, we can map a single server to multiple positions on the hash ring. We add _virtual replicas_ of the actual servers in the ring. The keys will be distributed more uniformly across the cache servers now.

![](https://i.imgur.com/sxs6Ek6.png)

Conclusion:
In distributed systems, as you scale up/down horizontally, building the cache each time is computationally expensive. Consistent Hashing minimizes the impact by remapping only a certain number of keys rather than all the keys as compared to the Hash Partitioning algorithm.

------
#hashing #consistent-hashing #cache-optimization
