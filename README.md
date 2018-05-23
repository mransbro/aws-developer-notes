# AWS Certified Developer - Associate 2018 Study notes

These are my study notes for the AWS Certified Developer - Associate certification. I have already passed the Solutions Architect - Associate exam so the notes might not cover topic if i feel i already know it well enough.

Table of Contents
=================

* [AWS Services 10,000 foot overview](#AWSServices10,000footoverview)


* [IAM](#IAM)

* [EC2](#EC2)

* [S3](#S3)

* [DynamoDB](#DynamoDB)

* [SQS](#SQS)

* [SNS](#SNS)

* [SWF](#SWF)

* [Elastic Beanstalk](#Elastic-Beanstalk)

* [CloudFormation](#CloudFormation)

* [AWS Shared Responsibility](#AWS-Shared-Responsibility)

* [Route 53](#Route-53)

* [VPC](##VPC)

[Exam Blueprint](http://awstrainingandcertification.s3.amazonaws.com/production/AWS_certified_developer_associate_blueprint.pdf)

# AWS Services 10,000 foot overview

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

Codestar - Project managaing code. Collorbation tool

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

Managed Services - AWS managed services

Elastic Transcoder - Video transcoding. Sizing videos for various devices

SageMaker - Deep learning

Comprehend - 

Deeplens - Physical hardware camera

Lex - Powers Alexa

Machine learning - 

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

QuickSight - Business inteligence tools

Data Pipeline - Moving data between AWS services

AWS Glue - Extracte format load

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

Step Functions - 

Amazon MQ - Rabbit MQ

SNS - Simple Notification Service

SQS - Simple Queue Service -  is a web service that gives you access to message queues that store messages waiting to be processed. With Amazon SQS, you can quickly build message queuing applications that can run on any computer. Amazon SQS can help you build a distributed application with decoupled components, working closely with the Amazon Elastic Compute Cloud (Amazon EC2) and other AWS infrastructure web services.

SWF - Simple Workflow Service

Connect - Contact centre as a service

Simple Email Service - Sending emails to customers

Alexa For Business - 

Chime - Google Hangout

Work Docs - Dropbox like service

WorkMail - Office365

Workspaces - VDI

AppStream 2.0 - App streaming

# IAM

[IAM FAQ](https://aws.amazon.com/iam/faqs/)

Users
Users have the choice of being given access to the management console and/or programmatic access. Access via the management console enables a password for the account. Enabling programmatic access enables an access key ID and secret access key. This can be used to access t

Groups
Groups allow you to apply policies to groups of users. Recommended to apply policies to groups even if it is for one user. Groups would be created to assign specific

Policies
Policies are JSON documents that contain permissions to AWS services. ie 

Roles

Secret

# EC2

[EC2 FAQ](https://aws.amazon.com/ec2/faqs/)

Access instance meta data at http://169.254.169.254/latest/meta-data/

# S3

[S3 FAQ](https://aws.amazon.com/s3/faqs/)

Four storage classes
1. S3 Standard
2. S3 Standard-Infrequent Access
3. S3 One Zone-Infrequent Access
4. Glacier

## Database Overview & Concepts

# DynamoDB

[DynamoDB FAQ](https://aws.amazon.com/dynamodb/faqs/)
	
NoSQL database
Stored on SSD

Spread across 3 geographically distinct data centres

2 Consistency models
1.Eventual consistent reads (default). Offers best read performance. Consistency across all copies of data is usually reached within a second.
2.Strongly consistent reads. Returns a result that reflects all writes that received a successful response prior to the read.

DynamoDB is priced on the storage size and its 'Provisioned Throughput'. Provisioned throughput is made up of read capacity units and write capacity units.
All reads rounded up to 4KB. Eventually consistent reads (default) consists of 2 reads per second. Strongly consistent reads consist of 1 read per second.
All writes are 1KB. All writes consist of 1 write per second.

Formula is (size of read rounded to 4KB chunk / 4KB) * no of items = read throughput
Divide by 2 if eventually consistent

If you exceed your provisioned throughput you will get a HTTP status code 400, ProvisionedThroughputExceededException.


# Simple Queue Service (SQS)

[SQS FAQ](https://aws.amazon.com/sqs/faqs/)

[SQS tutorial](https://aws.amazon.com/getting-started/tutorials/send-messages-distributed-applications/)


# Simple Notification Service (SNS)

[SNS FAQ](https://aws.amazon.com/sns/faqs/)

[SNS tutorial](https://aws.amazon.com/getting-started/tutorials/filter-messages-published-to-topics/)
	
After a message has been published to a topic it cant be deleted (recalled)

# Simple Workflow Service (SWF)

[SWF FAQ](https://aws.amazon.com/swf/faqs/)

# Elastic Beanstalk

[Elastic Beanstalk FAQ](https://aws.amazon.com/elasticbeanstalk/faqs/)

# CloudFormation

[CloudFormation FAQ](https://aws.amazon.com/cloudformation/faqs/)

# AWS Shared Responsibility

# Route 53

[Route53 FAQ](https://aws.amazon.com/route53/faqs/)

# Virtual Private Cloud (VPC)

[VPC FAQ](https://aws.amazon.com/vpc/faqs/)

By default all traffic between subnets is allowed

/16 is the largest CIDR block available

Subnets have a 1 to 1 mapping to an Availability Zone

1 Internet Gateway per VPC

