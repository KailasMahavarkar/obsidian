
```
A -> B -> C -> D ... microservice chain (assume each call takes 100ms)
```

## Problem:
Each service invocation adds its own latency to the total response time. For example, if each service adds 100ms, a chain of four services (A->B->C->D) will have a minimum total latency of 400ms.

## Majorly 3 things add cost when working with microservice chains:
1. the service itself can give response in `high` amount of time.
2. serialization and deserialization of data formats
3. synchronization of service calls 

## Mitigation Strategies

1. Asynchronous Processing - Implement asynchronous communication patterns to decouple services and reduce blocking waits.
2. using gRPC can offer faster latency (since it has support for http/2 which brings multiplexing multiple requests over a single connection and support protocol buffers (binary encoding) )
3. caching frequent responses
4. batch requests to reduce the number of invocations. 



# Asynchronous Processing
**Asynchronous Communication** allows a service to send a request and then immediately move on to other tasks without waiting for a response. The response is handled independently, often using callbacks, events, or message queues.

This simply involves, using message brokers and mechanisms like 

- **Producer:** A service that sends messages to the queue.
- **Consumer:** A service that retrieves messages from the queue and processes them.

## Q) how to handle the process completion (notification part or the part where you use response from previous request chain)

Callback Mechanism - When the consumer finishes processing the request, it sends a response back to the callback URL or executes the callback function (BeeQueue from NodeJS dont have support for this -> also http request don't have a callback mechanism inbuilt in themselves so question becomes how would you handle callbacks from single response (which was in JSON) -> what you can do instead is store a `callback endpoint` with each response)

About Notification part -> you can implement polling mechanism (used by whatsapp and others) thats checks for new messages every `x` seconds.


