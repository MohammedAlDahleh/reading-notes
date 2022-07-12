## Things I want to know more about

* AWS — Difference between SQS and SNS

- SQS vs SNS in AWS — Simple Notification Service and Simple Queue Service

- SQS and SNS are important components for scalable, large scale, distributed, cloud-based applications:

- SNS is a distributed publish-subscribe service.

- SQS is distributed queuing service.

* SNS (Simple Notification Service)

![SNS](https://miro.medium.com/max/502/1*mdUPKzrfJFuXa4d43KhKUQ.png)

- Amazon SNS is a fast, flexible, fully managed push notification service that lets you send individual messages or to bulk messages to large numbers of recipients. Amazon SNS makes it simple and cost effective to send push notifications to mobile device users, email recipients or even send messages to other distributed services.

- SNS is a distributed publish-subscribe system. Messages are pushed to subscribers as and when they are sent by publishers to SNS.

- SNS supports several end points such as email, sms, http end point and SQS. If you want unknown number and type of subscribers to receive messages, you need SNS.

- With Amazon SNS, you can send push notifications to Apple, Google, Fire OS, and Windows devices , as well as to Android devices in China with Baidu Cloud Push. You can use SNS to send SMS messages to mobile device users in the US or to email recipients worldwide.

* SQS (Simple Queue Service)

![SQS](https://miro.medium.com/max/700/1*7eL3udb6Cto4I9Ly1sN8oA.jpeg)

- Amazon SQS is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications.

- SQS is distributed queuing system. Messages are not pushed to receivers. Receivers have to poll SQS to receive messages. Messages can be stored in SQS for short duration of time (max 14 days).

- Messages can’t be received by multiple receivers at the same time. Any one receiver can receive a message, process and delete it. Other receivers do not receive the same message later. Polling inherently introduces some latency in message delivery in SQS unlike SNS where messages are immediately pushed to subscribers.

* Key Differences

* Entity Type
- SQS : Queue (similar to JMS, MSMQ).
- SNS : Topic-Subscriber (Pub/Sub system).

* Message consumption
- SQS : Pull Mechanism — Consumers poll messages from SQS.
- SNS : Push Mechanism — SNS pushes messages to consumers.

* Persistence
- SQS : Messages are persisted for some duration is no consumer available. The retention period value is from 1 minute to 14 days. The default is 4 days.
- SNS : No persistence. Whichever consumer is present at the time of message arrival, get the message and the message is deleted. If no consumers available then the message is lost.

- In SQS the message delivery is guaranteed but in SNS it is not.

* Consumer Type
- SQS : All the consumers are supposed to be identical and hence process the messages in exact same way.
- SNS : All the consumers are (supposed to be) processing the messages in different ways.

* Use Cases

 * Choose SNS if:
 - You would like to be able to publish and consume batches of messages.
 - You would like to allow same message to be processed in multiple ways.
 - Multiple subscribers are needed.

 * Choose SQS if:
 - You need a simple queue with no particular additional requirements.
 - Decoupling two applications and allowing parallel asynchronous processing.
 - Only one subscriber is needed.

 [AWS SQS vs SNS](https://medium.com/awesome-cloud/aws-difference-between-sqs-and-sns-61a397bf76c5)<br>
 [AWS SNS and SQS](https://www.youtube.com/watch?v=mXk0MNjlO7A)<br>
 [SQS and SNS Basics](https://www.youtube.com/watch?v=UesxWuZMZqI)<br>