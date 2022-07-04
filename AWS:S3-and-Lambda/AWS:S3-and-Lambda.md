## Things I want to know more about

# Amazon S3

- Object storage built to retrieve any amount of data from anywhere

* How it works
- Amazon Simple Storage Service (Amazon S3) is an object storage service offering industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can store and protect any amount of data for virtually any use case, such as data lakes, cloud-native applications, and mobile apps. With cost-effective storage classes and easy-to-use management features, you can optimize costs, organize data, and configure fine-tuned access controls to meet specific business, organizational, and compliance requirements.

* Use cases:

1. Build a data lake:

- Run big data analytics, artificial intelligence (AI), machine learning (ML), and high performance computing (HPC) applications to unlock data insights.

2. Back up and restore critical data
- Meet Recovery Time Objectives (RTO), Recovery Point Objectives (RPO), and compliance requirements with S3’s robust replication features.

3. Archive data at the lowest cost
- Move data archives to the Amazon S3 Glacier storage classes to lower costs, eliminate operational complexities, and gain new insights.

4. Run cloud-native applications
- Build fast, powerful mobile and web-based cloud-native apps that scale automatically in a highly available configuration.

# Lambda

* What is AWS Lambda?
- AWS Lambda is a serverless computing service provided by Amazon Web Services (AWS). Users of AWS Lambda create functions, self-contained applications written in one of the supported languages and runtimes, and upload them to AWS Lambda, which executes those functions in an efficient and flexible manner.
- The Lambda functions can perform any kind of computing task, from serving web pages and processing streams of data to calling APIs and integrating with other AWS services.

- The concept of “serverless” computing refers to not needing to maintain your own servers to run these functions. AWS Lambda is a fully managed service that takes care of all the infrastructure for you. And so “serverless” doesn’t mean that there are no servers involved: it just means that the servers, the operating systems, the network layer and the rest of the infrastructure have already been taken care of, so that you can focus on writing application code.


* How does AWS Lambda work?

- Each Lambda function runs in its own container. When a function is created, Lambda packages it into a new container and then executes that container on a multi-tenant cluster of machines managed by AWS. Before the functions start running, each function’s container is allocated its necessary RAM and CPU capacity. Once the functions finish running, the RAM allocated at the beginning is multiplied by the amount of time the function spent running. The customers then get charged based on the allocated memory and the amount of run time the function took to complete.

* Why is AWS Lambda an essential part of the Serverless architecture?
- When building Serverless applications, AWS Lambda is one of the main candidates for running the application code. Typically, to complete a Serverless stack you’ll need:

 - a computing service;
 - a database service; and
 - an HTTP gateway servic
 
* What are the most common use cases for AWS Lambda?

1. individual tasks run for a short time;
2. each task is generally self-contained;
3. there is a large difference between the lowest and highest levels in the workload of the application

* Creating AWS Lambda functions using the Serverless Framework:

1. Install Serverless Framework on your machine:
‍
__$ npm install serverless -g__
‍
2. Create a new service:
‍
__$ serverless__
‍
3. Add the resources your function needs to the serverless.yml file. Check out the AWS Intro doc for an example of this file and the list of options you can configure there.
‍
4. Add code to your service. See the Serverless AWS provider docs for specific steps you can follow to create your functions.
‍
5. Deploy to AWS by running the deploy step:
‍
__$ serverless deploy__

# Content Delivery Network (CDN)

* A Content Delivery Network (CDN) is a geographically distributed group of servers that work together to provide fast delivery of Internet content. A CDN allows for the fast transfer of data needed for loading Internet content including HTML pages, javascript files, stylesheets, images, and videos.

* What does this mean for an SMB?
- CDNs are something that larger companies are more likely to implement. The main reasons why company want to use CDNs are to improve Internet website load speeds, content delivery speeds, and to reduce the likelihood of falling victim to and improve defenses against Distributed Denial of Service attacks (DDoS).
 
- A smaller company probably doesn’t need to improve website load speeds with a CDN as they typically don’t have an overwhelming amount of traffic. A Distributed Denial of Service attack may pose a potential threat against gambling companies or other mid-to-large enterprises such as banks or defense contractors. DDoS attacks are rarely used against SMB’s unless they upset a hacker group. CyberHoot is not saying a denial of service attack won’t happen, but the cost of protection is too much for most SMBs to afford.

[AWS-S3](https://aws.amazon.com/s3/)<br>
[AWS-Lambda-Basics](https://www.serverless.com/aws-lambda)<br>
[CDN](https://cyberhoot.com/cybrary/content-delivery-network-cdn/)<br>