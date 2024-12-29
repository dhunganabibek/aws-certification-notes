# AWS Notes

## AWS Detective

operatates across multiple aws account and analyze the root cause of the issue.

## AWS Inspector

Automated vulnerabilities management service that scan ec2 and container for software vulnerabilities and unintented network exposure.
Have host(ec2) and network(vpc) assesments.

## AWS Guard Duty

Threat detection service. detect compromised instance and account compromise.

## AWS Network Firewall

Physical firewall for vpc.

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

## SG to instance and NACL

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


## sScaling by ASG:

Target Tracking Scaling: Maintains a target metric value.
Step Scaling: Scales based on the severity of metric breaches.
Simple Scaling: Scales based on a single metric threshold.
Scheduled Scaling: Scales based on a predefined schedule.