
A queue is like a buffer. You can put messages into a queue, and you can retrieve messages from a queue. The software that puts messages into a queue is called a message producer and the software that retrieves messages is called a message consumer.

![](https://i.imgur.com/aqvhMc7.png)


## topic publisher & topic Subscriber
A topic is like a broadcasting station. You can publish messages to a topic, and anyone interested in these messages can subscribe to the topic. Then, the interested parties are notified about the published messages. The software that broadcasts topics is called a **topic publisher** and the software that subscribes to broadcasts is called a **topic subscriber**.

![](https://i.imgur.com/V91AB7o.png)


**When should you use messaging?**
1. **Service-to-service communication** -> set up a queue and have the frontend website code send messages to the queue and have the backend CRM service to consume them.

2. **Asynchronous work item backlogs** -> Let’s say a hotel booking system needs to cancel a booking and this process takes a long time (from a few seconds to a minute). You can execute the cancellation synchronously, but then you risk annoying the customer who has to wait for the webpage to load. You can also track all pending cancellations in your database and keep polling and executing cancellations. Alternatively, you can put a message into a queue and have the same hotel booking system consume messages from that queue and perform asynchronous cancellations.

3. **[[State Change Notifications]]** -> the inventory system can publish notifications about stock changes to a topic and any interested program can subscribe to learn about those changes. 



-----
resoruces:
https://aws.amazon.com/blogs/compute/building-scalable-applications-and-microservices-adding-messaging-to-your-toolbox/