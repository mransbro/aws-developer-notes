# AWS Certified Developer - Associate 2018 Study notes

These are my study notes for the AWS Certified Developer - Associate certification. I have already passed the Solutions Architect - Associate exam so the notes might not cover topic if i feel i already know it well enough.

## AWS Services 10,000 foot overview

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

SQS - Simple Queue Service - decouple infrastructre 

SWF - Simple Workflow Service

Connect - Contact centre as a service

Simple Email Service - Sending emails to customers

Alexa For Business - 

Chime - Google Hangout

Work Docs - Dropbox like service

WorkMail - Office365

Workspaces - VDI

AppStream 2.0 - App streaming

## Identity Access Management (IAM)

Users
Users have the choice of being given access to the management console and/or programmatic access. Access via the management console enables a password for the account. Enabling programmatic access enables an access key ID and secret access key. This can be used to access t

Groups
Groups allow you to apply policies to groups of users. Recommended to apply policies to groups even if it is for one user. Groups would be created to assign specific

Policies
Policies are JSON documents that contain permissions to AWS services. ie 

Roles

Secret

## EC2

Access instance meta data at http://169.254.169.254/latest/meta-data/

## S3

## Database Overview & Concepts

## DynamoDB
	
NoSQL database
Stored on SSD

Spread across 3 geographically distinct data centres

2 Consistency models (Leave as default )
	i. Eventual consistent reads (default). Offers best read performance. Consistency across all copies of data is usually reached within a second.
	ii. Strongly consistent reads. Returns a result that reflects all writes that received a successful response prior to the read.

## Simple Queue Service (SQS)



## Simple Notification Service (SNS)
	
After a message has been published to a topic it cant be deleted (recalled)

## Simple Workflow Service (SWF)

## Elastic Beanstalk

## CloudFormation

## AWS Shared resposibility

## Route 53 & DNS

## Virtual Private Cloud (VPC)

By default all traffic between subnets is allowed

/16 is the largest CIDR block available

Subnets have a 1 to 1 mapping to an Availablity Zone

1 Internet Gateway per VPC

