# AWS Certified Developer - Associate Study notes

These are my study notes for the AWS Certified Developer - Associate certification. I have already passed the Solutions Architect - Associate exam so the notes might not cover topics if i feel i already know it well enough.

Table of Contents
=================

* [AWS Services 10,000 foot overview](#AWS-Services)

* [IAM](#iam)

* [EC2](#EC2)

* [S3](#S3)

* [DynamoDB](#DynamoDB)
  
* [SQS](#Simple-Queue-Service-SQS)

* [SNS](#SNS)

* [SWF](#SWF)

* [Elastic Beanstalk](#Elastic-Beanstalk)

* [CloudFormation](#CloudFormation)

* [AWS Shared Responsibility](#AWS-Shared-Responsibility)

* [Route 53](#Route-53)

* [VPC](#VPC)

* [CloudFront](#CloudFront)

* [Lambda](#Lambda)

[Exam Blueprint](http://awstrainingandcertification.s3.amazonaws.com/production/AWS_certified_developer_associate_blueprint.pdf)

# AWS-Services

EC2 - Elastic Compute Cloud virtual machines

Lightsail - Provisiong service - Very hands off

Elastic Container Service - running containers such as docker at scale

Lambda - Serverless functions

Elastic Beanstalk - Easier route for developers to get up and running with their cloud

ElastiCache - Cache common searches in front of DB servers

S3 - Key pair object storage kept in buckets

EFS - NFS can be mounted on multiple instances

Glacier - Archival storage

Snowball - Hardware appliance to transfer data between on-prem and AWS

Storage gateway - Virtual appliances that live on-prem and replicate to AWS

RDS - MySQL, MSSQL, Aurora, PostGreSQL

DynamoDB - NoSQL

RedShitft - Data warehousing

AWS Migration Hub - Dashboard that lets you track your application migration

Application Discovery Service - tracks your applications dependencies

Database Migration Service - Migrate DBs to AWS

Server Migration Service

VPC Virtual Private Cloud

Cloudfront - Content Delivery Network (CDN) caches content to make it available quicker to the end user.

Route53 - Amazon's DNS service

API Gateway - Creating API's for your own services

Direct Connect - Network peering between yourself and AWS

Codestar - Project managing code. Collorbation tool

Codecommit - Source control service

Codebuild - Complies and test your code

Codedeploy - Automates your application deployment

Codepiple - CDS

X-Ray - Used to debug your serverless application

Cloud9 - Online IDE

CloudWatch - Monitoring

CloudFormation - Infrastructure as Code

CloudTrail - API logging

Config - Monitor AWS account config

OpsWorks - Config management using Chef or Puppet

Service Catalog - Managing IT services approved for use

Systems Manager - Patch maintenance
Trusted Advisor - Gives advice on security, cost

Elastic Transcoder - Video transcoding. Sizing videos for various devices


Lex - Powers Alexa


Polly - Text to speech

Rekognition - Analyse images and video

Amazon translate - Language translate

Amazon Transcribe - Automatic speech regonition

Athena - run SQL queries against S3 buckets

Elastic Map Reduce - managed software framework used to process large data sets in a distributed computing environment. Used for data analysis, web indexing, data warehousing, machine learning, financial analysis, scientific simulation etc. EMR supports workloads based on Hadoop, Apache Spark, Presto and Apache HBase.

CloudSearch

ElasticSearch Service

Kinesis - Ingesting large amounts of data

Kinesis Video Streams - Ingesting lots of video streams

Data Pipeline - Moving data between AWS services

IAM - Identity and Management access

Cognito - Mobile Device authentication using federated accounts Facebook etc

Guard Duty -

Inspector - Anaylse instance security using agent

Macie - Scans S3 buskets for personal iD numbers

Certificate manager - Free SSL certs

CloudHSM - Hardware security module which store keys

Directory services - Connect AWS to onside AD

WAF Web application firewall - L7 firewall

Shield - DDOS mitigation

Artifcat - AWS compliance reports

SNS - Simple Notification Service

SQS - Simple Queue Service -  is a web service that gives you access to message queues that store messages waiting to be processed. With Amazon SQS, you can quickly build message queuing applications that can run on any computer. Amazon SQS can help you build a distributed application with decoupled components, working closely with the Amazon Elastic Compute Cloud (Amazon EC2) and other AWS infrastructure web services.

SWF - Simple Workflow Service

Simple Email Service - Sending emails to customers

WorkMail - Office365

Workspaces - VDI

# IAM

[IAM FAQ](https://aws.amazon.com/iam/faqs/)

Users
Users have the choice of being given access to the management console and/or programmatic access. Access via the management console enables a password for the account. Enabling programmatic access enables an access key ID and secret access key. This can be used to access t

### Groups

Groups allow you to apply policies to multiple users. Recommended to apply policies to groups even if it is for one user.

* Users can be members of multiple groups
* Groups cannot be nested

Policies
Policies are JSON documents that contain permissions to AWS services. ie

Roles

Secret

## Security Token Service (STS)

* Grants users limited and temporary access to AWS resources.
* 3 sources:
    1. Federation (often Active Directory)
        * Uses SAML
        * SSO allows users to log in to AWS Console without assigning IAM credentials
    2. Federation with mobile app
        * Use Facebook/Amazon/Google or other openID provider
    3. Cross account access
        * Lets users from one AWS account access resources in another

### Active Directory Federation

# EC2

[EC2 FAQ](https://aws.amazon.com/ec2/faqs/)

Access instance meta data at http://169.254.169.254/latest/meta-data/

* Scipts can be run from the user data section when creating an instance

## Load Balancers

* There are 3 types of load balancer; Application, Network and Classic. Application is used to route HTTP/HTTPS (L7) traffic. Network and Classic are used to route TCP (L4) traffic.

    1. Application - TLS termination
    2. Network - Extermeme performance and static IP
    3. Classic (also refered to as Elastic Load Balancer ELB) - 

* Sticky sessions are a mechanism to route requests to the same target in a target group. This is useful for servers that maintain state information in order to provide a continuous experience to clients.

# S3

[S3 FAQ](https://aws.amazon.com/s3/faqs/)

### Storage classes

* Buckets can contain objects of different storage classes

1. S3 Standard
2. S3 Standard-Infrequent Access - for data that is less frequently accessed but requires rapid access when needed. Availability drops to 99.9% and there is a data retrieval charge of $0.01 / GB.
3. S3 One Zone-Infrequent Access - Offers similar performance as other S3 classes but stores data redundantly within an Availability Zone not across Availability Zones.
4. Glacier - used for archiving data.

* No limit on number of objects in a bucket
* Largest object size is 5TB
* Smallest object size is 0 bytes
* Largest upload in a single PUT is 5GB. (Objects larger than 100MB should be uploaded with multipart uploader)
* A bucket cannot contain a bucket

* Need to delete large amounts of

* S3 provides read-after-write consistency for PUTS of new objects.
* S3 offers eventual consistency for overwrite PUTS and DELETES.

* If you expect more than 300 PUT/LIST/DELETE requests per second or more than 800 GET request per second raise a support request with AWS to prepare for the workload.

* Event notifications can sent in response to actions such as PUTs, POSTs, COPYs or DELETEs, Messages can be sent through SNS, SQS or Lambda.

* CORS (Cross-Origin resource sharing) enables a way for client web applications loaded in one domain to interact with resources in a different domain.

### Encryption

* Server-Side
1. KMS-Managed Encryption keys
2. Amazon S3-Managed Encryption keys
3. Customer-Provided Encryption keys

* Client-Side
1. AWS KMS-managed customer master key
2. Client-side master key

# DynamoDB

[DynamoDB FAQ](https://aws.amazon.com/dynamodb/faqs/)

NoSQL database
Stored on SSD

Spread across 3 geographically distinct data centres

Consistency models

1. Eventual consistent reads (default). Offers best read performance. Consistency across all copies of data is usually reached within a second.
2. Strongly consistent reads. Returns a result that reflects all writes that received a successful response prior to the read.

## Indexes

Two types of primary keys available;
Single Attribute - partition key (Customer no, driver license etc)
Composite - partition key & sort key (Customer no & date range)

Local Secondary Index
    same partition key but different sort key
    Can only be created when creating a table

Global Secondary Index
    Different partition key and different sort key
    Can be created at table creation or added later

## Streams

Four options for streams only 1 can be selected

1. Keys Only - Only the key attributes of the modified item
2. New image the entire item, as it appears after it was modified
3. Old image - the entire item, as it appeared before it was modified
4. New and old images - both the new and the old images of the item

* Max 24 hour storage
* Can have Lambda triggered from streams

If a new item is added to the table, the stream captures an image of the entire item, including all attributes
if item is updated, stream captures the before and after image of any attributes that were modified
if item is deleted the stream captures an image of the item before deletion

## Query vs Scan

* Query - a query find items in a table using only the primary key.
* Scan - a scan operation examines every item in the table. By default a scan returns all of the data attributes for every item. You can use the ProjectionExpression parameter so that Scan only returns some of the attributes.

Query is more efficient than scan

Batch get item for more efficient queries of large items

### Provisioned Throughput

DynamoDB is priced on the storage size and its 'Provisioned Throughput'. Provisioned throughput is made up of read capacity units and write capacity units.
All reads rounded up to 4KB. Eventually consistent reads (default) consists of 2 reads per second. Strongly consistent reads consist of 1 read per second.
All writes are 1KB. All writes consist of 1 write per second.

Formula is (size of read rounded to 4KB chunk / 4KB) * no of items = read throughput
Divide by 2 if eventually consistent

If you exceed your provisioned throughput you will get a HTTP status code 400, ProvisionedThroughputExceededException.

# Simple Queue Service SQS

[SQS FAQ](https://aws.amazon.com/sqs/faqs/)

[SQS tutorial](https://aws.amazon.com/getting-started/tutorials/send-messages-distributed-applications/)

SQS is a pull based messaging service.

Allows the 'decoupling' of components of an application.

FIFO queues are not supported in all regions. Currently only: US East (Ohio), US East (N. Virginia), US West (Oregon), and EU (Ireland) regions.

The maximum amount of time that a message can live in a SQS queue is 14 days. The retention period can be configred to be anywhere betweeen 1 minute and 14 days. The default is 4 days. Once the message retention limit is reached, your messages are automatically deleted.

SQS messages must be between 1 and 256 KB in size. Billed in 64KB chunks.

SQS supports two types of pull based polling:

**Short polling** - SQS returns a response immediately, even if there is no message in the queue
**Long polling** - doesn’t return a response until a message arrives in the message queue, or the long poll times out. Can be cheaper then short polling as it can reduce the number of empty receives.
In almost all cases, long polling is preferable to short polling. One case you might want to use short polling is if you application uses a single thread to poll multiple queues.

When a consumer receives a message from the SQS queue, it stays in the SQS queue. The message must be deleted by the consumer once the message has been fully processed. To prevent other conumers from receiving the message, SQS sets a Visibility Timeout, which is the period of time where SQS prevents other consuming components from receiving and processing the message.

First 1 million requests are free, then $0.50 for every million after.

# Simple Notification Service (SNS)

[SNS FAQ](https://aws.amazon.com/sns/faqs/)

[SNS tutorial](https://aws.amazon.com/getting-started/tutorials/filter-messages-published-to-topics/)
After a message has been published to a topic it cant be deleted (recalled)

SNS is a messaging service that 'pushes' messages to clients.

Messages protocols:

* Application
* SMS text message
* Email
* Email-JSON
* AWS SQS
* HTTP
* HTTPS

SNS can be used with SQS to fan messages out to multiple queues.

SNS uses Topics to send messages. To receive messages published to a topic you have to subscribe. Once a message is published, SNS attempts to deliver to every endpoint that is subscribed.

Messages can be customised by protocol type.

Messages are stored reduntly across mulitple AZ's.

# Simple Workflow Service (SWF)

[SWF FAQ](https://aws.amazon.com/swf/faqs/)

* Workers are programs that interact with SWF to get tasks, process received tasks and return the results.
* Decider is a program that controls the coordination of tasks.

Tasks assigned only once and never duplicated.

Domains - workflow and activity types and the workflow execution itself are all scoped to a domain. Domains isolate a set of types, executions, and task lists from other within the same account. You can register a domain by using the console or SWF API. Using JSON.

## SWF vs SQS

* SWF presents task oriented API whereas SQS offers message oriented API.
* SWF ensures that a task is assigned only once. With SQS you need to handle duplicated messages and may also need to ensure that a message is processed only once.
* SWF keeps track of all tasks and events in an application. With SQS you need to implement your own application-level tracking.

# Elastic Beanstalk

[Elastic Beanstalk FAQ](https://aws.amazon.com/elasticbeanstalk/faqs/)

* Can have multiple versions of your applications (Dev/Test)
* Your applications can be split into tiers. Frontend/backend etc
* able to update application
* can update your configuration ie change instance type behind the app
* Updates can be 1 instance at a time or % of instances or immutable

### Languages

* Apache Tomcat for Java
* Apache HTTP server for PHP
* Apache HTTP Server for Python
* Nginx or Apache HTTP for Node.js
* Passenger or Puma for Ruby
* Microsoft IIS 7.5, 8.0 and 8.5 for .NET
* Java SE
* Docker
* Go

# CloudFormation

[CloudFormation FAQ](https://aws.amazon.com/cloudformation/faqs/)

A cloudFormation is made up of the following sections:

__Resources__ (required) - specify the stack resources and their properties such as an EC2 instance or a S3 bucket. You can refer to resources in the Resources and Outputs sections of the template.

__Metadata__ (optional) - objects that provide additional information about the template.

__Parameters__ (optional) - specifies values that you can pass in to your template at runtime (when you create or update a stack). You can refer to parameters in the Resources and Outputs sections of the template.

__Mappings__ (optional) - a mapping of keys and associated values that you can use to specify conditional parameter values, similar to a lookup table. You can match a key to a corresponding value by using the Fn::FindInMap intrinsic function in the Resources and Outputs section.

__Conditions__ (optional) - defines conditions that control whether certain resources are created or whether certain resource properties are assigned a value during stack creation or update. For example, you could conditionally create a resource that depends on whether the stack is for a production or test environment.

__Transform__ (optional) - for serverless applications (also referred to as Lambda-based applications), specifies the version of the AWS Serverless Application Model (AWS SAM) to use.

__Outputs__ describes the values that are returned whenever you view your stack’s properties. For example, you can declare an output for an S3 bucket name and then call the aws cloudformation describe-stacks AWS CLI command to view the name.
The only required section in a Cloudformation template is the Resources section

* Automatic rollback on error is enabled by default.
* Use function Fn:GetAtt to output data
* Stacks can wait for applications to be provisioned using the 'waitCondition'

# AWS Shared Responsibility

IaaS - Customer manages OS and above including security and patches. AWS manages hypervisor and below including physical infrastructure.

SaaS – AWS manages everything except user credentials.

# Route-53

[Route53 FAQ](https://aws.amazon.com/route53/faqs/)

* Limit of 50 domain names - speak to AWS support to adjust.

* CNAME (Canonical Name) can be used to resolve one domain another
* A Record (Address Record) for resolving a domain name to an IP address
* Alias records are an AWS / Route 53 specific term, similar to CNAME with the key distinction that CNAMEs can't be used on the zone apex (root domain i.e. cnames could be used against sofa.furniture.com, but not against furniture.com - for this you'd need to use either an A Record or Alias record)

* In the exam always choose Alias over CNAME. Amazon dont charge to resolve Alias records and they can be used to map naked domain apex to an ELB.

## Routing Policies

* Simple - default policy, used when there is only one resource.
* Weighted - send a specified amount of traffic to certain resources. ie for every 10 requests send 70% to us-east-1 and 30% to eu-west-1.
* Latency - used to send traffic to lowest latency region. This requires you to create an A record for each region you want the latency to be evaluated against.
* Failover - failover allows you to have an active/passive design. Using health checks to assess whether to send traffic to the primary or secondary resource. A health check can use Cloud watch alarms, other health checks or simply use a TCP connection to an IP or domain name.
* Geolocation - used to send traffic to a particular region based on source location. ie Customers in a Eurozone country always get routed to a server with prices in Euros.

# VPC

[VPC FAQ](https://aws.amazon.com/vpc/faqs/)

* By default all traffic between subnets is allowed

* /16 is the largest CIDR block available

* Subnets have a 1 to 1 mapping to an Availability Zone

* 1 Internet Gateway per VPC

* You cannot change the ip range of a VPC

* Elastic IP addresses (EIPs) are public IP addresses that

* Elastic Network interface

# CloudFront

* Content Delivery Network (CDN). Provides content quicker to customers by caching it in edge locations. ie customer 1 watches a video from s3. s3 bucket is in Ireland but user is in Sydney. The content flows Ireland -----> Sydney. CloudFront caches it locally near Sydney so the second time its accessed the content flows, CloudFront Sydney -> Sydney.

* Edge locations can be used for write as well as read.

* Objects are cached for ther life of their TTL. TTL can be 0 seconds to 365 days. Default is 24 hours.

* Origin can be S3, EC2, ELB, Route53 and non AWS server ie on-prem

* Restrict viewer access by signed URL or Signed Cookies

* Restrict content based on geo location (whitelist and blacklist)

# Lambda
* Compute service allows you to run code without provisioning and managing servers. Under the hood are EC2 Instances managed by AWS.

* Lambda is stateless and event driven. 

* If we increase memory, cpu usage will get increase. Max memory limit is 3008 MBs. Max execution timeouts is 300

* Temporary objects downloaded by lambda are stored in /tmp directory. 

* Alias can be use to manage different versions for lambda. You can change version behind lambda.

* Use AWS Lambda Environment Variables to pass operational parameters to your function.

* Lambda Optimization Tips: Avoid using recursion, keep deployment size minimum, install only dependecies that is required, keep your function logic outside handler. (source: https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html)
