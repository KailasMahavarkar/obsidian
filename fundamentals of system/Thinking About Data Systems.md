There are datastores that are also used as message queues (Redis), and there are message queues with database-like durability guarantees (Apache Kafka).

**People who build message queues will claim that their system offers one of three delivery guarantees—that each message you put into the queue will be delivered:**

- at-least once.
- at-most once.
- exactly once.

> This is limitation of redis remember it does not offer data delivery guarantee in message queue





----
 #redis