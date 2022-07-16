## Things I want to know more about

# AWS: API, Dynamo and Lambda

* AWS API Gateway Overview

- Amazon API Gateway is a managed service that allows developers to define the HTTP endpoints of a REST API or a WebSocket API and connect those endpoints with the corresponding backend business logic. It also handles authentication, access control, monitoring, and tracing of API requests.

- Why is Amazon API Gateway an important part of the Serverless ecosystem ?

- Within the Serverless ecosystem, API Gateway is the piece that ties together Serverless functions and API definitions. Being able to trigger the execution of a Serverless function directly in response to an HTTP request is the key reason why API Gateway is so valuable in Serverless setups: it enables a truly serverless architecture for web applications.

- Why is Amazon API Gateway an important part of the Serverless ecosystem ?

- Within the Serverless ecosystem, API Gateway is the piece that ties together Serverless functions and API definitions. Being able to trigger the execution of a Serverless function directly in response to an HTTP request is the key reason why API Gateway is so valuable in Serverless setups: it enables a truly serverless architecture for web applications.

* How API Gateway Works

- What are the some benefits of using Amazon API Gateway ?

1. Efficient API development
2. Performance at any scale
3. Cost savings at scale
4. Easy monitoring
5. Flexible security controls
6. RESTful API options

- What two API types might you choose from ?
1. RESTful APIs.
2. WEBSOCKET APIs.

* AWS DynamoDB Guide

- Amazon DynamoDB: Fast, flexible NoSQL database service for single-digit millisecond performance at any scale

- DynamoDB is a particularly good fit for the following use cases

- Applications with large amounts of data and strict latency requirements.

- Serverless applications using AWS Lambda.

- Data sets with simple, known access patterns

- Use cases:
1. Develop software applications.
2. Create media metadata stores.
3. Deliver seamless retail experiences.
4. Scale gaming platforms.

* Dynamoose:

-Dynamoose: is a modeling tool for Amazon's DynamoDB. Dynamoose is heavily inspired by Mongoose, which means if you are coming from Mongoose the syntax will be very familar.

- Key Features:

- Type safety
1. High level API
2. Easy to use syntax
3. Ability to transform data before saving or retrieving documents
4. Strict data modeling (validation, required attributes, and more)
5. Support for DynamoDB Transactions
6. Powerful Conditional/Filtering Support
7. Callback & Promise support 

[AWS API Gateway Overview](https://www.serverless.com/amazon-api-gateway)<br>
[AWS API Gateway](https://aws.amazon.com/api-gateway/)<br>
[AWS DynamoDB Guide](https://www.dynamodbguide.com/what-is-dynamo-db/)<br>
[AWS DynamoDB](https://aws.amazon.com/dynamodb/)<br>
[Dynamoose](https://dynamoosejs.com/getting_started/Introduction)<br>