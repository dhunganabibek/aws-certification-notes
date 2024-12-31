# AWS Notes

## AWS Detective

Operatates across multiple aws account and analyze the root cause of the issue.

## AWS Inspector

Automated vulnerabilities management service that scan ec2 and container for software vulnerabilities and unintented network exposure.
Have host(ec2) and network(vpc) assesments.

## AWS Guard Duty

Threat detection service. detect compromised instance and account compromise.

## AWS Network Firewall

Physical firewall for vpc.

## AWS Security Hub

loud Security Posture Management service that performs security best practice checks, aggregates alerts, and enables automated remediation
a single place to view security realted alerts from services like (GuardDuty, Inspector, Macie, AWS Firewall Manager)

## WAF

WAF protect on layer 7 for DDOS and layer  3 and 4 is protected by shield.
WAF also protect from SQL injection and cross site scripting.
Also block specific counytry or IP address.

## AWS Audit Manager

Automated service that provides report specific to compliance.

## AWS artifact

Single source for compliance related information.

## system manager

can manage both on premise and AWS compute
Automation: custom playbook
Run Command: excute command on managed compute with out SSH and RDP
Session Manager: Connect to managed comput with out SSH and RDP.

## Instance profile

Used to attach IAM role to EC2 instance.

## changing securtiy group of instance

possible when instance is running or stopped

## User pools and Identity Pools

users pools: user diretory for sign on and sign up.
identity pools: grant user access to aws services.

## NACL

stateless (SG being stateful)
like firewall for subnet
default NACL: allow all inbound and outbound traffic
custom NACL: deny all traffic
rule applied from low to high. And eager apply (even if it is denied later)

## SG

statful
only allow rule.
Default all inbound blocked and all out boun allowed

## AWS Quantum Ledger Database

Immutable and cryptrographycally verifiable.

### neptune

graph datanbase

## metadata and userdate

Instance Metadata:

meta data: <http://169.254.169.254/latest/meta-data/>  
User Data: <http://169.254.169.254/latest/user-data>

## EKS Distro

kibernetes distro used by aws eks
<https://github.com/aws/eks-distro>

## Prometheus and Grafana

Prometheus - monitoring tool
Grafana - visualization tool

## step of authorizing cognito through third party like facebook

1. **Authenticate and get token from facebook**
2. **Exchange that facebook token to cognito token**
3. **Use Cognito token to obatain temporay aws credentials from Identity Pool**
4. **use temporary aws crendentials to access aws services**

## Amazon Appflow

automate exchange of data between saas venders and aws service like s3. can transfer 100 GB per flow.

## ALB vs NLB

| Feature                     | Network Load Balancer (NLB)             | Application Load Balancer (ALB)       |
|-----------------------------|-----------------------------------------|---------------------------------------|
| OSI Model Layer             | Layer 4 (Transport Layer)               | Layer 7 (Application Layer)           |
| Protocol Support            | TCP, UDP, TLS                           | HTTP, HTTPS, WebSocket                |
| Performance                 | High performance, low latency           | Good performance, more features       |
| Use Case                    | Ideal for extreme performance           | Ideal for web applications and microservices |
| Health Checks               | Supports TCP, HTTP, HTTPS health checks | Supports HTTP, HTTPS health checks    |
| Sticky Sessions             | Not supported                           | Supported                             |
| SSL Termination             | Supported                               | Supported                             |
| Target Types                | IP addresses, instance IDs              | IP addresses, instance IDs, Lambda functions |
| Path-Based Routing          | Not supported                           | Supported                             |
| Host-Based Routing          | Not supported                           | Supported                             |
| WebSocket Support           | Not supported                           | Supported                             |
| Cross-Zone Load Balancing   | Supported                               | Supported                             |
| Logging                     | VPC Flow Logs                           | Access Logs                           |
| Pricing                     | Generally lower cost                    | Generally higher cost                 |

## AWS Snowball Family

1. SnowCone - 8TB

2. Snowball Edge (both storage and compute)

    - Snowball Edge  Compute optimized (42 TB, 52 vCPU)
    - Snowbal Edge Storage Optmized (80 Tb 40  vCPU)

3. Snowmobile - 100 PB (long shipping container)

## Upload to s3

Single object can be of max 160gb. Beyound that use  s3 multipart upload.

## Message Broker  vs Streaming plantform

|Message Broker |  Streaminng Platform   |
|----------------------------------------|---------------------------------|
| Decoupling and routing messages        |  Real time data  processing     |
| Short term                             | long term                       |
| Push based(RAbbit MQ), SQS (pull based)|  pull based  (Kafka)            |

## kinesis Data stream vs Data Firehose

|Data stream                        |                   Data Firehose               |
|-----------------------------------|-----------------------------------------------|
| real time streaming (processing)  | real time data delivery                       |
| custom app/lambda for processing  | managed service( no custim code)              |
| data retention (configurable)     | data rentention (short, until delivered)      |
| Highly scalable (shards)          | automatic scalable                            |
| custom code for delivery          | automatic delver to s3, redshift, elastic search , splunk|

## services used by alexa

lex - chatbot
polly - text to speech
transacribe - speech to text

## SG to instance and NACL5 GB of standard Amazon S3 storage is provided with the AWS Free Tier's always free offer.

1 instance - 5SG
1 subnet - 1 NACL
Also, you can not delete default security group
You can not modify NACL rule with `* All Traffic Deny`
IG is attached to VPC (not subnets)

## Amazon Fraud Detector

AI service build to detect fraud in your data

## AWS Firewall Manager and AWS Network Firewall

| AWS Firewall Manager | AWS Network Firewall|
|----------------------|---------------------|
| organization level   | VPC level           |

## SES

S3 Notification can not use SES directly. It can use SQS, SNS and lambda as destination

## Multi AZ database deployment

Use synchronous standby (write to both primary and replica simultaneously, so might take some time for writing).
If you want multi region, you can use READ repilcas or Aurora Global database.

### 1. Simple Routing

- Directs traffic to a single resource without any special routing logic.

### 2. Weighted Routing

- Distributes traffic across multiple resources based on assigned weights to balance load or perform A/B testing.

### 3. Latency Routing

- Routes traffic to the resource that provides the lowest latency for the user to improve performance.

### 4. Failover Routing

- Routes traffic to a primary resource and automatically fails over to a secondary resource if the primary becomes unavailable.

### 5. Geolocation Routing

- Routes traffic based on the geographic location of the user to provide localized content or comply with regulatory requirements.

### 6. Geoproximity Routing (Traffic Flow Only)

- Routes traffic based on the geographic location of users and resources, with the ability to shift traffic by specifying a bias.

### 7. Multi-Value Answer Routing

- Returns multiple IP addresses in response to DNS queries to provide simple load balancing and health checks.

## Readily available in EC2 cloud watch

- CPU
- Disk
- Network
- StatusCheckFailed
- But not memory (for memory you have to go custom metrics)

## Elastic Network Interface

It can be attached to EC2 in VPC.

Hot Attach: Attaching an ENI to an instance while it is running.
Warm Attach: Attaching an ENI to an instance while it is stopped.
Cold Attach: Attaching an ENI to an instance when it is being launched.

Public ENI: Attached to the instance to handle incoming HTTP requests from the internet.
Private ENI: Attached to the same instance to handle secure communication with a backend database within the VPC.

## AWS AppSync

build scalable applications, including real-time updates and offline capabilitis using GraphQL.

## Dedicated Host vs Dedicated instancce

| Feature                | Dedicated Host                                      | Dedicated Instance                                  |
|------------------------|-----------------------------------------------------|-----------------------------------------------------|
| **Definition**         | Entire physical server dedicated to you.            | Instances on hardware dedicated to you.             |
| **Control**            | Full control over instance placement.               | No control over instance placement.                 |
| **Billing**            | Billed per host.                                    | Billed per instance.                                |
| **Use Case**           | Compliance, licensing, control over hardware.       | Physical isolation without hardware control.        |
| **Isolation**          | Yes, with control over the server.                  | Yes, but no control over the server.                |

- **Dedicated Host**: Like having your own physical server (full control, like a VPS).
- **Dedicated Instance**: Like having multiple computers on the same dedicated hardware (isolated but no control over the hardware).

## Reddshift Spectrum

 allowing you to run SQL queries directly against exabytes of unstructured data in Amazon S3 data lakes

## Memcached vs Redis

| Feature                | Amazon ElastiCache for Redis                        | Amazon ElastiCache for Memcached                    |
|------------------------|-----------------------------------------------------|-----------------------------------------------------|
| **Service Type**       | Managed Redis service on AWS.                       | Managed Memcached service on AWS.                   |
| **Data Model**         | In-memory data structure store (strings, hashes, lists, sets, sorted sets, etc.). | In-memory key-value store.                          |
| **Persistence**        | Supports data persistence with snapshots and AOF (Append-Only File). | No built-in persistence, purely in-memory.          |
| **High Availability**  | Supports replication, automatic failover, and Multi-AZ deployments. | No built-in high availability, requires manual setup. |
| **Scalability**        | Supports sharding and replication for horizontal scaling. | Supports horizontal scaling with sharding.          |
| **Backup and Restore** | Automated backups, snapshots, and point-in-time recovery. | No built-in backup and restore features.            |
| **Use Case**           | Suitable for use cases requiring complex data structures, persistence, and high availability. | Suitable for simple caching use cases with high performance and low latency. |
| **Security**           | Integrated with AWS security features like VPC, IAM, and encryption. | Integrated with AWS security features like VPC and IAM. |
| **Performance**        | Optimized for read-heavy and write-heavy workloads with complex data structures. | Optimized for simple, high-performance caching.     |
| **Cost**               | Pay-as-you-go pricing with managed service fees.    | Pay-as-you-go pricing with managed service fees.    |

### Simplified Explanation

- **Amazon ElastiCache for Redis**: Managed Redis service on AWS, suitable for complex data structures, persistence, and high availability.
- **Amazon ElastiCache for Memcached**: Managed Memcached service on AWS, suitable for simple, high-performance caching use cases.

## AWS Batch

Fully managed service for running batch computing workloads with dynamic provisioning of EC2 instances.

## Scaling by ASG

Target Tracking Scaling: Maintains a target metric value.
Step Scaling: Scales based on the severity of metric breaches.
Simple Scaling: Scales based on a single metric threshold.
Scheduled Scaling: Scales based on a predefined schedule.

## data replicatin in Database

synchronous - Multi-AZ deployment
asynchronus - read repilcas

## types of Endpoints

| Endpoint Type                  | Description                                                                 | Use Case                                                                                     | Example Services                                      |
|--------------------------------|-----------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|-------------------------------------------------------|
| **Interface Endpoints**        | ENIs with private IPs for AWS services.                                      | Private connections to AWS services within your VPC.                                         | Amazon S3, Amazon EC2, AWS Lambda, Amazon SNS         |
| **Gateway Endpoints**          | Route table entries for AWS services.                                        | Private connections to AWS services like S3 and DynamoDB within your VPC.                    | Amazon S3, Amazon DynamoDB                            |
| **Gateway Load Balancer Endpoints** | Combine Gateway Load Balancer with an endpoint.                              | Deploy and manage virtual appliances like firewalls and intrusion detection systems.         | Custom network and security appliances                |
| **VPC Endpoints**              | Private connections between VPC and AWS services.                            | Securely connect to AWS services and third-party services without using the public internet. | Amazon S3, Amazon EC2, AWS Lambda, Amazon SNS         |
| **Regional Endpoints**         | Endpoints specific to a particular AWS region.                               | Access AWS services within a specific region.                                                | Most AWS services                                     |
| **Edge Endpoints**             | Part of the AWS global network, used for services like CloudFront.           | Improve performance and availability by routing traffic through the AWS global network.      | Amazon CloudFront, AWS Global Accelerator             |
| **PrivateLink Endpoints**      | Private connectivity between VPCs, AWS services, and on-premises applications. | Access services hosted on AWS privately without exposing your traffic to the public internet. | Custom services, Amazon S3, Amazon EC2                |

## EFS types| Volume Type            | Purpose                                             | Performance                                          | Use Case                                            | Cost                                                 |

| Volume Type            | Purpose                                             | Performance                                          | Use Case                                            | Cost                                                 |
|------------------------|-----------------------------------------------------|-----------------------------------------------------|-----------------------------------------------------|------------------------------------------------------|
| **gp3**                | General-purpose workloads with balanced performance and cost. | Baseline 3,000 IOPS and 125 MB/s, up to 16,000 IOPS and 1,000 MB/s. | Boot volumes, small to medium-sized databases, development and test environments. | Lower cost with predictable performance.             |
| **gp2**                | General-purpose workloads with balanced performance and cost. | Baseline 3 IOPS/GB, up to 16,000 IOPS.              | Boot volumes, small to medium-sized databases, development and test environments. | Cost-effective for a wide range of workloads.        |
| **io2**                | Mission-critical applications requiring high performance and high durability. | Up to 64,000 IOPS and 1,000 MB/s per volume.        | Large databases, critical business applications, workloads requiring high IOPS. | Higher cost for higher performance and durability.   |
| **io1**                | I/O-intensive applications requiring high performance. | Up to 64,000 IOPS and 1,000 MB/s per volume.        | Large databases, critical business applications, workloads requiring high IOPS. | Higher cost for higher performance.                  |
| **st1**                | Frequently accessed, throughput-intensive workloads. | Baseline 40 MB/s per TB, up to 500 MB/s per volume. | Big data, data warehouses, log processing, streaming workloads. | Lower cost compared to SSD volumes, optimized for throughput. |
| **sc1**                | Infrequently accessed, throughput-intensive workloads. | Baseline 12 MB/s per TB, up to 250 MB/s per volume. | Infrequently accessed data, cold data storage, large volumes of data with low access frequency. | Lowest cost, optimized for infrequent access.        |
| **Magnetic**           | Legacy workloads with infrequent access.            | Lower performance compared to SSD and HDD volumes.  | Infrequently accessed data, legacy workloads.       | Lower cost, but less efficient compared to newer volume types. |

## Amazon keyspaces

 managed, scalable, and highly available Cassandra-compatible database service.

## types of scaling

 | Scaling Type           | Purpose                                             | Use Case                                            | Key Features                                        | Example                                             |
|------------------------|-----------------------------------------------------|-----------------------------------------------------|-----------------------------------------------------|-----------------------------------------------------|
| **Predictive Scaling** | Uses machine learning to forecast traffic and capacity needs. | Predictable traffic patterns (e.g., daily or weekly cycles). | Automatically adjusts capacity in anticipation of predicted traffic spikes and drops. | Automatically scales resources in anticipation of weekday traffic spikes and weekend drops. |
| **Scheduled Scaling**  | Adjusts the number of instances based on a predefined schedule. | Predictable workloads that follow a regular schedule. | Specify exact times to increase or decrease the number of instances. | Scale out to 10 instances at 8 AM and scale in to 2 instances at 6 PM every day. |
| **Dynamic Scaling**    | Automatically adjusts the number of instances based on real-time changes in demand. | Variable and unpredictable workloads.               | Uses scaling policies based on CloudWatch alarms to trigger scaling actions. | Scale out when CPU utilization exceeds 70% and scale in when it drops below 30%. |
| **Manual Scaling**     | Allows you to manually adjust the number of instances. | Scenarios where you want full control over scaling actions. | Manually increase or decrease the number of instances. | Manually scale out to 5 instances during a planned event and scale in to 2 instances afterward. |

## EBS snapshots

Amazon Data lifecycle manager to automate the creation of EBS snapshots.

## NAT Gateway vs NAT instance

## NAT Gateway vs NAT Instances

Provide internet access to private subnet through NAT

| Feature                | NAT Gateway                                      | NAT Instances                                      |
|------------------------|--------------------------------------------------|----------------------------------------------------|
| **Managed Service**    | Fully managed by AWS                             | Requires user management                           |
| **Scalability**        | Automatically scales up to handle traffic        | Requires manual scaling                            |
| **Availability**       | Highly available and fault-tolerant              | Requires configuration for high availability       |
| **Performance**        | Consistent performance                           | Performance depends on instance type               |
| **Cost**               | Higher cost due to managed service               | Potentially lower cost but requires management     |
| **Setup**              | Easy to set up                                   | Requires more configuration                        |
| **Security Groups**    | Cannot be associated with security groups        | Can be associated with security groups             |
| **Elastic IP**         | Automatically assigned                           | Must be manually assigned                          |
| **Use Case**           | Recommended for most use cases                   | Suitable for custom configurations and lower cost  |

## RDS MultiAZ Deployment

During primary failover, CName is swiched.

## AWS Outpost

It allows you to run AWS services locally on your own hardware while maintaining a consistent hybrid experience.

## AWS Application Migration Service (MGN)

is a highly automated lift-and-shift (rehost) solution that simplifies, expedites, and reduces the cost of migrating applications to AWS

## AWS Wavelength

 embeds AWS compute and storage services within 5G networks

## redis

It have function like ZRANGE and ZRANK to sort and rank the data

## Code Deploy

- Application Stop
- Download Bundle
- Before  Install
- Install
- After Install
- Application Start
- Validate Service

## CPU increase in Lambda

You can not do this dorectly. Instead increase memory which will also increase CPU.

## Viewer Protocol Policy

define protocol viewer can use to access cloudfront content.
options: http and https, redirect http to https and https only.

## Identity center

- Centralozed Access Management (SS0)
- integrate with identity providers(Microsoft Active Directory, Okta) using SAML 2.0
- can integrate woith directory service for SAML (AD connector)

## Server Side Encryption in S3

``` json
    "Version": "2012-10-17"
    "Statement": [
        "Effect": "Deny",
        "Principal": "*",
        "Action":"s3:PutObject",
        "Resource": "arn:aws:s3:::/bucket-name/*",
        "Condition:{
            "StringNotEquals":{
                "s3:z-amz-server-side-encryptio": "AES256"
            }
        }
    ]
```

making s3 sp

```bash
aws s3 cp myfile s3://bucket-name/ --sse AES256
```

using put object using boto3

```python
import boto3

s3 = boto3.client('s3')

s3.upload_file(
    'myfile',
    'bucket-name',
    'myfile.txt',
    ExtraArgs={'ServerSideEncryption': 'AES246'}

)
```

Note: upload_file is higher level abstraction of put_object and handle (retry, progress tracking and multipart upload automatically for big files)

## Encrypting AMI

You can not encrpt the AMI after being created. You can copy the AMI, specify to encrypt the copy.
Basically, AMI region specific. If you neeed in another region, copy it.

## AWS Codepipeline

You can create test stage with test action before deoloyment.

## AWS Opswork

Configuration Management Service that provide managed instance of chef and puppet.

## Types of key in Dynamodb

1. Primary Key

    - Partition/Hash key
    - Composite key (Partition and Sort/Range key)

2. Secondary keys

    - Global Secondary Index 
    - Local Secondary Index

| Feature                        | Global Secondary Index (GSI)                          | Local Secondary Index (LSI)                           |
|--------------------------------|-------------------------------------------------------|-------------------------------------------------------|
| Partition Key                  | Can be different from the base table's partition key  | Must be the same as the base table's partition key    |
| Sort Key                       | Optional, can be different from the base table's sort key | Must be different from the base table's sort key      |
| Query Scope                    | Across all partitions                                 | Within a single partition                             |
| Write Capacity Units (WCU)     | Separate from the base table                          | Shared with the base table                            |
| Read Capacity Units (RCU)      | Separate from the base table                          | Shared with the base table                            |
| Maximum Number per Table       | Up to 20 GSIs per table                               | Up to 5 LSIs per table                                |
| Use Case                       | Different access patterns and query requirements      | Alternate sort keys for querying within the same partition |
| Consistency                    | Eventually consistent reads by default, can be strongly consistent | Strongly consistent reads                             |
| Creation Time                  | Can be created at any time                            | Must be created at the time of table creation         |

## Work flows in state function

| Feature                        | Standard Workflows                              | Express Workflows                               |
|--------------------------------|-------------------------------------------------|-------------------------------------------------|
| Execution Duration             | Up to 1 year                                    | Up to 5 minutes                                 |
| Execution Start Rate           | Up to 2,000 per second                          | Up to 100,000 per second                        |
| State Transition Rate          | Up to 4,000 per second                          | Up to 100,000 per second                        |
| Billing                        | Based on the number of state transitions        | Based on the number of executions and duration  |
| Use Case                       | Long-running, durable workflows                 | High-volume, short-duration workflows           |
| Error Handling                 | Built-in retry and error handling               | Built-in retry and error handling               |
| Execution History              | Detailed execution history available            | Limited execution history available             |
| Monitoring                     | CloudWatch Logs, CloudWatch Metrics, X-Ray      | CloudWatch Logs, CloudWatch Metrics, X-Ray      |
| State Machine Execution        | Synchronous and asynchronous                    | Synchronous and asynchronous                    |
| State Machine Definition       | Amazon States Language (ASL)                    | Amazon States Language (ASL)                    |
| Integration with AWS Services  | Full integration with AWS services              | Full integration with AWS services              |
| Pricing Model                  | Pay per state transition                        | Pay per execution and duration                  |
| Ideal For                      | Complex workflows with long-running tasks       | High-volume event processing and short tasks    |

## Deplooyment using aws cloud formation

- use create-stack-set and create-stack-insatnce to deploy stack set in muliple region.
Structue

```yaml
AWSTemplateFormatVersion:
Description:
Parameters: input
Resources:  is only mandatory
Output: 
```

## Cloudlog Insights

Enable you to interactively search and analyze the log.

## using X-Ray with EC2 or onpremise server

need to install X-Ray SDK and X-Ray Daemon


