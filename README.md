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


