---
title: "AWS"
metaTitle: "AWS | DevNotes"
metaDescription: "A AWS land"
---



# AWS Certified Solutions Architect Associate
## Exam
Orion: **About The Exam**
Time: 130 minutes
Questions: 65
2 minutes / question
MCQ - Choose 1 or 2 answers out of 4
Cost: $150

## CSA Terminology
Orion: Appendix > Terminology
* High Availablity
* Fault Tolerance
* Scalibility
	* Vertical (Increase capacity of single instance)
	* Horizontal (Add or Terminate the number of instances)
* Elasticity
	* Easy of system's ability to scale/change/adapt
* Cost Efficient
* Secure


## Well Architected Framework
Well architected framework is a design guideline to guide AWS developer to build systems are certain compliant.
e.g.
This framework suggests to build systems that are 
* Reliable
	* Able to recover from failure and mitigate disruptions
	* Amazon CloudWatch
* Secure
* Cost Efficient
* Resource Efficient
* Operationally Excellent

## Account and Services Layer
AWS can be interacted through multiple interfaces:
* AWS Console
* AWS CLI
* AWS SDK

### Account Management
* Root Account users are email account holders which are root
* Regular users use a username to login and are authenticated through IAM. IAM allows to give or revoke permissions to these users.

**!important**
Have Multifactored Auth (MFA) enabled to secure the users

## IAM - Identity and Access Management
IAM is used to create users and grant specific privilidges to them and to specific AWS services.
Root User: The person who has full access and is the owner of the AWS account.
Users usually access AWS through internet and get authenticated through IAM
**IAM is a global service**

### IAM Groups
IAM > Groups > Create Group
* Group Name
* Policies
* Assign Users

Managing User policies individually can be quite hectic, a better way to manage user permissions is IAM Groups.
Create IAM groups and give the group specifc permissions to that group and add users to it.

### IAM Roles
IAM > Roles > Create Roles

Grant access to AWS from other AWS services
Other services can assume a role, it's temporary, and temporariliy grants access to these services. So if an EC2 instance needs to access an S3Bucket, the EC2 can assume the role of S3BucketAdmin

You don't save anything permanently so you don't get compromised.



### IAM API Access Keys
IAM > 
CLI or SDK has to provide API Key which are attached to certain users, and are needed to authenticate a user

API Keys are just text
* Access Key ID - Available on dashboard
* Secret Access Key - Private Key

### STS - Security Token Service
An endpoint which returns a set of API keys, once these expire they can never be used again.
Get API keys for 12-36 hours

### Add User
Services > IAM > Add User
* Add Username
* Give acess type
* Add password
* Add the users to group
* Each user is assigned a unique ARN

#### Create strong password
By default there is no strong password policy, go to account settings > Manage password policy.

Follow the principle of least privlidge, only give as little privilidge to a user as necessary.

Take a look at **Best Practices** in Orion > IAM Essentials


### IAM Policies
IAM>Policies>Create Policy
A JSON document that formally states the permissions provided to a user
* By default everything is implicitly denied
* Allow or Deny permissions
* Deny trumps Allow

### Identity Federation
* Custom Identity Provider
* SAML

## AWS Organizations
Allows to make a Root account to handle multiple AWS accounts


## EC2
Elastic Cloud Compute

* Scalable Virtual Servers in the cloud called **instances**
* Come in multiple sizes and preferrences

To run an EC2
* Choose AMI (Amazon Machine Image) - Operating system and other settings
* Instance Type -- Hardware (CPU, Memory, Space)
* Network Interface -- (public, private, or elastic IP address)
* Storage -- Elastic Block Store (Persistent) or Instance Store (Temporary)

### EC2 Placement Group
* Cluster Placement Groups
* Troubleshooting Placement Groups
! No extra charge for placement groups

### EC2 Purchasing Options
* On-Demand
	*	Cheapest way to do if infrequent usage
	*	Can give out of memory error
* Reserved
	* Cheaper than on-demand if continuous usage - Get discounts
	* IF reserved, won't get out of memory error

## EFS Essentials - Elastic File System
* Shared filesystem across EC2 instances
* Elastic storage -- will increase or decrease as needed
* Fully manages, no maintenance needed
* Can be acess by one or more  EC2 instances at same time

## Physical and Networking Layer
### AWS Region
An AWS region will contain 2 or more availablity zones. The actual physical data centers are grouped in these availablity zones and each availability zone within a region is separated by tens of miles.

Launch Application in multiple availablity zones so even if one goes down the other stays up.

Each region has different pricing due to location specific costs.

### Edge Location
Edge location is different from AWS Regions, there are two services that run on these edge locations.

#### Route53
Service that provides DNS lookups, for resolving domains, to make that lookup fast, Route53 runs on edge locations all around the world.

#### Cloudfront
A content delivery network (CDN) -- Cache frequenty accessed data.
If some content is being accessed frequently by users, it is cached on CF and it is access fast.

CF also has
* AWS Shield
* AWS WAF
* S3 Transfer
* API Gateway

### Regional Edge Cache
If some cached content is not being accessed frequently in CF, instead of just deleting it, CF will store it in a regional edge cache. The reason being that if it just deletes it, next time a user tries to access it, it will take a long time. So instead it ejects it into a Regional Edge Cache and accesses it from there and make it fastum fast.



## VPC - Virtual Private Cloud
VPC is designed to resemble: Private on-premise data centers, private corporate network

* VPC are regional networks spanning multiple availablity zones
* A VPC is housed within a chosen AWS region

VPC has security groups which can allow or deny traffic


* Tenancy determines whether or not the EC2 instance will be on its own host machine or shared with other customers. By default it's shared.


### Internet Gateway
Internet gatway is a component of VPC which connects our VPC to the internet. 
Horizontally scalable, redundant and highly available
Can be attached or detached from VPC, but if VPC is already launched, may not be able to detach


## ELB - Elastic Load Balancing

Service provided by AWS to automatically scale up or down other services
Come between the 

Can do health checks, will only send traffic to healthy ec2 instances



## Databases
With relational databases, you need to vertically scale it.
*	Schema-full, structured data
*	Are ACID Compliant

With NoSQL, you can horizontally scale it into clusters.
* Schema-less, nonstructed data
* Are not ACID compliant


### RDS - Relational Database Service
#### Aurora 
Amazon's homegrown SQL server, 5x faster than other implementations
MySQL and PostgreSQL Compatible
Continuous Backup
Replication Lag of Single Digit Milliseconds
Upto 15 read replicas

* Amazon Aurora Serverless
* Autoscaling
* No management
* Scales to Zero
* Pay as you go


RDS Multi-AZ Failover
AWS will automatically switch DNS record from primary instance to secondary instance


#### DynamoDB
NoSQL fully managed database

Manages provisioning and scaling

Has a lot of redundancy

Document type -- can save JSON type documents


#### Neptune
DynamoDB uses proprietery APIs, Neptune uses opensource -- 

Neptune is a NoSQL db, and is graph type. Can store up to 64TB of data.


#### ElastiCache
Used for offloading other databases -- Get result once and store it in Elasticache and then use it from there instead of querying the db again and again
* Cache Hit -- Cache Miss
*  Engines
	* Memcached
		* Easy to scale
		* Simple model
		* Multithreaded
	* Redis
		* Complex datatypes
		* Multi-AZ failover
		* Data Persistence
		* Encryption


#### Redshift - OLAP - Online Analytics Processing
Optimized for analytics -- Data warehouse
Other systems feed it
Easily scalable
Each compute node can do 1.6 Petabyte of data
Forked from PostgreSQL
Amazon QuickSight

Redshift Spectrum
Can query Exabytes of data


## S3 - Simple Storage Service
S3 is a regional service. Data will be stored in a single region, but will be fault tolerant, copied across multiple availablity places

Infinite Scalability -- pay for only what you store
5TB max object size

### Buckets
S3 has containers to store your data called Buckets -- they contain a grouping  of information and have sub names

#### Versioning
Versioning is done at the bucket level and it changes the bucket behaviour. So if the bucket is deleted, it can still be recovered. Once versioning is activated it can't be deactivated.
* Cross Region Replication

### Lifecycle policies
Set of rules to automate the migration of an object



## VPN - Virtual Private Network

## CloudFront
CloudFront runs on over a 100 edge locations, CF is a Content Delivery Network
Can integrate with Route53
Can cache stuff, time can be set for it TTL, TTL can be set to 0 for dynamic content
Instead of doing POST/PUT directly to an S3 bucket, it can be done to CF and then CF can upload to S3

Other services that run on edge locations: 
* Amazon Rout53
* AWS WAF - Web Application Firewall
* AWS Shield
* Lambda


## Security

### Security of the cloud
AWS maintains the security of the cloud.

### Security in the cloud
Security in the cloud is the responsibility of the user.




## Resources
* [Orion Papers](https://interactive.linuxacademy.com/diagrams/TheOrionPapers.html)
* Read the whitepapers - Specifically: Architecting for the cloud: AWS Best Practicies
[https://aws.amazon.com/architecture/well-architected/](https://aws.amazon.com/architecture/well-architected/)
[https://d1.awsstatic.com/whitepapers/AWS_Cloud_Best_Practices.pdf](https://d1.awsstatic.com/whitepapers/AWS_Cloud_Best_Practices.pdf)
