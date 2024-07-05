![](https://i.imgur.com/13t6nDq.png)


![](https://i.imgur.com/H1yaA7R.png)



![](https://i.imgur.com/ToMNTDK.png)

> "We will put individual SQS queues in front of our downstream microservices and use SNS to fan out messages to these queues."

So, Fanout here refers to SNS sending fanout messages to SQS ..... which SQS will later interact and further process this request

> Note: this does not refer to way of polling (which could be confused since.... in system design architecture ... polling refers to way of fetching notification which is a actually refers to bottle neck)


# Avoiding Fanout Bottlenecks

**Fanout**: In this context, fanout refers to sending a message from SNS to multiple SQS (Simple Queue Service) queues. Each service has its own SQS queue to receive messages from SNS.

**Potential Bottlenecks**:

- If many messages are sent from SNS to multiple SQS queues, it can create a bottleneck.
- This is because SQS queues may get overwhelmed with too many messages at once, leading to delays or dropped messages.

### Managing Fanout and Avoiding Bottlenecks

1. **Message Filtering**:
    - Use message attributes and filtering to ensure that each SQS queue only receives relevant messages. This reduces the number of messages each queue has to handle.
2. **Batching Messages**:
    - Send messages in batches to reduce the number of individual messages. This helps in managing the load more efficiently.
3. **Auto-Scaling**:
    - Implement auto-scaling for the services processing messages from SQS queues. This ensures they can handle increased loads dynamically.
4. **Throttling and Rate Limiting**:
    - Use throttling to limit the number of messages sent from SNS to SQS. This helps prevent overwhelming the queues.
5. **Monitoring and Alerts**:
    - Set up monitoring and alerts to track the performance and health of your queues. This helps in identifying and addressing bottlenecks quickly.



# Resources:
https://www.linkedin.com/pulse/build-fan-out-architecture-aws-using-snssqslambda-katuri-bhuvanesh/


--------
#system-design-concepts