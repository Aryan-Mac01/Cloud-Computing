# Cloud Computing — Complete Notes

> A comprehensive guide covering Cloud Computing fundamentals and AWS services.

---

## Table of Contents

1. [Introduction to Cloud Computing](#1-introduction-to-cloud-computing)
2. [Cloud Service Models](#2-cloud-service-models)
3. [Cloud Deployment Models](#3-cloud-deployment-models)
4. [Core Cloud Concepts](#4-core-cloud-concepts)
5. [Virtualization in the Cloud](#5-virtualization-in-the-cloud)
6. [Networking in the Cloud](#6-networking-in-the-cloud)
7. [Cloud Security](#7-cloud-security)
8. [Cloud Storage](#8-cloud-storage)
9. [Cloud Use Cases](#9-cloud-use-cases)
10. [Introduction to AWS](#10-introduction-to-aws)
11. [Core AWS Services](#11-core-aws-services)
12. [AWS IAM](#12-aws-iam)
13. [AWS Resource Management](#13-aws-resource-management)
14. [AWS Monitoring Tools](#14-aws-monitoring-tools)
15. [AWS Pricing and Support](#15-aws-pricing-and-support)
16. [AWS Security and Compliance](#16-aws-security-and-compliance)
17. [AWS DevOps and Automation](#17-aws-devops-and-automation)
18. [How Cloud Storage Works Internally](#18-how-cloud-storage-works-internally)
19. [AWS IAM Policy Syntax Explained](#19-aws-iam-policy-syntax-explained)

---

## 1. Introduction to Cloud Computing

### Definition

Cloud computing is the delivery of computing services — servers, storage, databases, networking, software, analytics and intelligence — over the internet. You pay only for what you use, avoiding the cost of owning and maintaining physical infrastructure.

### The 5 Key Characteristics (NIST Definition)

| Characteristic | What it means |
|---|---|
| On-demand self-service | Provision resources instantly without human interaction from the provider |
| Broad network access | Accessible from anywhere over the internet via standard devices |
| Resource pooling | Provider's resources are shared across many customers (multi-tenant) |
| Rapid elasticity | Scale up or down quickly based on demand |
| Measured service | Pay only for what you use, like a utility bill |

### Benefits

- No upfront hardware cost
- Pay-as-you-go pricing
- Scale instantly up or down
- Global reach in minutes
- Always on the latest software and hardware
- High availability built in

### Challenges

- Vendor lock-in risk
- Data privacy and sovereignty concerns
- Dependency on internet connectivity
- Cost management complexity
- Compliance requirements vary by region

---

## 2. Cloud Service Models

The three service models define how much you manage vs how much the provider manages.

```
On-Premises    IaaS           PaaS           SaaS
─────────────────────────────────────────────────
You manage:    You manage:    You manage:    You manage:
  App            App            App            Usage only
  Data           Data           Data
  Runtime        Runtime
  OS             OS
  Servers        ──────────────────────────────
  Storage        Provider manages everything below
  Networking
```

### IaaS — Infrastructure as a Service

Rent raw computing resources. You install and manage the OS, middleware, and software.

- **Examples:** AWS EC2, Azure Virtual Machines, Google Compute Engine
- **Best for:** System admins, DevOps engineers, custom OS configurations
- **You manage:** OS, runtime, applications, data
- **Provider manages:** Servers, storage, networking, virtualization

### PaaS — Platform as a Service

A ready-made platform. You write code and deploy — the platform handles everything underneath.

- **Examples:** Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service
- **Best for:** Developers who just want to deploy code without managing servers
- **You manage:** Application and data only
- **Provider manages:** Everything below the application layer

### SaaS — Software as a Service

Fully finished applications delivered over the internet. Zero installation, zero maintenance.

- **Examples:** Gmail, Salesforce, Microsoft 365, Slack, Google Photos
- **Best for:** End users, no technical knowledge required
- **You manage:** Usage and your data only
- **Provider manages:** The entire stack

### Shared Responsibility Model

Security responsibilities are split between you and the provider. The line shifts depending on service model:

- **IaaS** → you are responsible for most things
- **PaaS** → shared responsibility
- **SaaS** → provider responsible for almost everything

---

## 3. Cloud Deployment Models

### Public Cloud

Infrastructure owned and operated by a third-party provider, shared across many organisations.

- **Examples:** AWS, Microsoft Azure, Google Cloud
- **Cost:** Lowest (pay-per-use)
- **Control:** Least
- **Best for:** Startups, variable workloads, general applications

### Private Cloud

Dedicated infrastructure for a single organisation. Can be on-premises or hosted by a third party.

- **Examples:** On-site data centers, VMware private cloud
- **Cost:** Highest
- **Control:** Most
- **Best for:** Banks, healthcare, government — industries with strict compliance requirements

### Hybrid Cloud

Combination of public and private cloud. Sensitive workloads stay private, scalable workloads run on public cloud. Connected via VPN or Direct Connect.

- **Cost:** Medium
- **Flexibility:** High
- **Complexity:** High
- **Best for:** Enterprises with mixed workload requirements

### Community Cloud

Shared infrastructure for organisations with common concerns — same industry, same compliance requirements. Cost is split between members.

- **Examples:** Government agencies sharing infrastructure
- **Best for:** Sector-specific organisations with shared compliance needs

---

## 4. Core Cloud Concepts

### Scalability

The ability to increase or decrease resources to handle growing workloads.

- **Vertical scaling (Scale Up):** Give the existing machine more power (bigger CPU, more RAM)
- **Horizontal scaling (Scale Out):** Add more machines to distribute the load

### Elasticity

Automatically adding resources when load spikes and removing them when load drops — without human intervention. You only pay for what you actually use at any given moment.

> **Scalability vs Elasticity:** Scalability is the *ability* to scale. Elasticity is the *automatic act* of scaling dynamically in real time. A system can be scalable but not elastic if you have to manually add servers.

### Agility

The speed at which you can provision new infrastructure. In cloud, a new server can be ready in minutes instead of weeks of hardware procurement. This enables fast experimentation and iteration.

### Reliability

The system performs its intended function correctly and consistently. Measured as uptime percentage. Cloud providers guarantee this via SLAs (Service Level Agreements).

### High Availability (HA)

The system remains operational with minimal downtime. Achieved through redundancy — multiple servers across multiple locations. Key metric: **99.99% availability = only 52 minutes of downtime per year**.

Achieved via:
- Redundant hardware and power
- Multiple availability zones
- Load balancing
- Automatic failover

### Disaster Recovery (DR)

The plan and capability to recover IT systems after a disaster — outage, cyberattack, or natural disaster.

| Metric | Full Name | Meaning |
|---|---|---|
| **RPO** | Recovery Point Objective | How much data loss is acceptable? If RPO = 1 hour, backups must run every hour. |
| **RTO** | Recovery Time Objective | How long can the system be down? If RTO = 4 hours, you must restore within 4 hours. |

---

## 5. Virtualization in the Cloud

Virtualization creates a software-based version of computing resources. One physical machine can run many virtual machines simultaneously. This is the foundation technology that makes cloud computing possible.

### Hypervisor

Software that creates and manages virtual machines. Sits between physical hardware and the VMs.

| Type | Runs on | Examples | Used for |
|---|---|---|---|
| Type 1 (Bare Metal) | Directly on hardware | VMware ESXi, Hyper-V | Data centers, production |
| Type 2 (Hosted) | On top of an OS | VirtualBox, VMware Workstation | Developer laptops |

### Virtual Machines (VMs)

A complete computer (CPU, RAM, storage, OS) running entirely in software. Each VM is completely isolated from others on the same physical host.

- Includes a full OS copy
- Strong isolation between VMs
- Takes minutes to boot
- Size: Gigabytes

### Containers

Package an app and its dependencies together without a full OS. Share the host OS kernel.

- Much lighter than VMs
- Start in seconds
- Size: Megabytes
- Less isolation than VMs
- **Most popular tool:** Docker
- **Orchestration:** Kubernetes

### VM vs Container Comparison

| Feature | Virtual Machine | Container |
|---|---|---|
| OS included | Yes — full OS per VM | No — shares host OS kernel |
| Size | Gigabytes | Megabytes |
| Startup time | Minutes | Seconds |
| Isolation | Strong (separate kernel) | Process-level |
| Best for | Different OS needs, strong security | Microservices, fast deployments |
| Examples | AWS EC2, Azure VMs | Docker, Kubernetes, AWS ECS |

---

## 6. Networking in the Cloud

### Key Concepts

| Concept | What it does | Real-world analogy |
|---|---|---|
| IP Address | Identifies a device on a network | Your home address |
| DNS | Translates domain names to IP addresses | Contacts app on your phone |
| Router | Directs traffic between networks | Road junction with signposts |
| VNet / VPC | Private isolated network in the cloud | A private gated community |
| Load Balancer | Distributes traffic across multiple servers | Cashier directing customers to open tills |
| VPN | Encrypted tunnel to cloud over public internet | A private road through a public city |
| Direct Connect | Dedicated physical private line to cloud | A private highway only you use |

### Virtual Networks (VNet / VPC)

A logically isolated section of the cloud where you launch your resources. You control:
- IP address ranges (CIDR blocks)
- Subnets (public and private)
- Route tables
- Internet gateways

### Subnets

A VNet is divided into subnets:
- **Public subnet** — resources here have internet access (web servers, load balancers)
- **Private subnet** — no direct internet access (databases, internal services)

> **Security best practice:** Never put your database in a public subnet. Always keep it in a private subnet.

### Load Balancing

Distributes incoming requests across multiple servers so no single server is overwhelmed. If one server fails, traffic automatically routes to healthy servers.

Types in AWS:
- **ALB (Application Load Balancer)** — HTTP/HTTPS, Layer 7
- **NLB (Network Load Balancer)** — TCP, Layer 4, ultra-high performance
- **GLB (Gateway Load Balancer)** — for security appliances

---

## 7. Cloud Security

### Cloud vs On-Premises Security

In cloud, the security model shifts. **Identity becomes the new perimeter** — instead of protecting a physical network boundary, you protect access based on identity.

### IAM — Identity and Access Management

Controls who can do what in your cloud environment.

| Component | Purpose |
|---|---|
| Users | Individual identities (people or applications) |
| Groups | Collections of users sharing the same permissions |
| Roles | Temporary identity that can be assumed by services or cross-account access |
| Policies | JSON documents defining what actions are allowed or denied |

> **Principle of Least Privilege:** Grant only the minimum permissions needed to perform a specific task — nothing more.

### Encryption

| Type | When | Example |
|---|---|---|
| Data at rest | When stored on disk | AES-256 encryption on S3 |
| Data in transit | When moving over the network | HTTPS / TLS 1.3 |
| Data in use | While being processed | Newer technology (confidential computing) |

### Compliance Standards

| Standard | Industry |
|---|---|
| GDPR | European data protection |
| HIPAA | Healthcare (USA) |
| PCI-DSS | Payment card industry |
| ISO 27001 | General information security |
| SOC 2 | Service organisation controls |

### Shared Responsibility Model

```
Provider is responsible FOR the cloud:
  Physical hardware, data centers, network infrastructure

You are responsible IN the cloud:
  Your data, your user access, your app configuration, OS patches (in IaaS)
```

---

## 8. Cloud Storage

### Three Storage Types

#### Block Storage

Divides data into fixed-size blocks. OS treats it like a physical hard drive. Lowest latency.

- **Best for:** Databases, OS boot volumes, high-performance apps
- **AWS:** EBS (Elastic Block Store)
- **Azure:** Managed Disks

#### Object Storage

Stores data as objects — each with data, metadata, and a unique ID. Infinitely scalable. Access via HTTP.

- **Best for:** Photos, videos, backups, logs, static websites
- **AWS:** S3 (Simple Storage Service)
- **Azure:** Blob Storage
- **Google:** Cloud Storage

#### File Storage

Traditional folder-and-file hierarchy. Multiple servers can access simultaneously.

- **Best for:** Shared drives, home directories, content management
- **AWS:** EFS (Elastic File System)
- **Azure:** Azure Files

### Storage Comparison

| Feature | Block | Object | File |
|---|---|---|---|
| Structure | Fixed-size blocks | Flat key-value | Hierarchical folders |
| Access method | Direct disk | HTTP API / URL | NFS / SMB |
| Performance | Highest | Medium | Medium |
| Scalability | Limited | Virtually unlimited | Large but bounded |
| Cost per GB | Higher | Lowest | Medium |

### Data Lifecycle Management

Automatically move data between storage tiers as it ages to save costs:

```
Hot tier    → Frequently accessed, most expensive  (current data)
     ↓ after 30 days
Cool tier   → Less accessed, cheaper               (older data)
     ↓ after 90 days
Archive tier → Rarely accessed, very cheap         (compliance records)
               (hours to retrieve)
```

---

## 9. Cloud Use Cases

| Use Case | Description | Key Requirement |
|---|---|---|
| Web and mobile apps | Host websites, APIs, mobile backends | Scalability, global CDN |
| Big data and analytics | Process petabytes without owning hardware | Compute on demand |
| Backup and DR | Offsite backups, fast restoration | Reliability, low RPO/RTO |
| AI and machine learning | GPU clusters, pre-built AI APIs | Specialised hardware |
| DevOps and CI/CD | Automated build, test, deploy pipelines | Speed and automation |
| IoT | Receive and process data from millions of devices | Real-time processing |

### Industry Applications

| Industry | Cloud use case |
|---|---|
| Healthcare | Electronic health records, medical imaging, telemedicine |
| Banking | Fraud detection AI, real-time transactions |
| Retail | Recommendation engines, Black Friday auto-scaling |
| Education | Online learning platforms, virtual classrooms |
| Government | Citizen services, national databases |
| Media | Video streaming, content delivery (Netflix) |

---

## 10. Introduction to AWS

### What is AWS?

Amazon Web Services is the world's most comprehensive cloud platform, launched in 2006. It offers 200+ fully featured services from data centers globally. Holds approximately 31% of the global cloud market share.

### Global Infrastructure

| Component | Count | Purpose |
|---|---|---|
| Regions | 33+ | Geographic locations (e.g. ap-south-1 = Mumbai) |
| Availability Zones | 105+ | Isolated data centers within a region |
| Edge Locations | 450+ | CDN cache points close to end users |

### Regions vs Availability Zones

- A **Region** is like a city (e.g. Mumbai)
- **Availability Zones** are separate buildings within that city
- AZs are physically separated but connected by low-latency private fiber
- Deploy across multiple AZs for high availability
- Deploy across multiple Regions for disaster recovery

```
Region: ap-south-1 (Mumbai)
├── AZ: ap-south-1a (Data center cluster A)
├── AZ: ap-south-1b (Data center cluster B)
└── AZ: ap-south-1c (Data center cluster C)
```

---

## 11. Core AWS Services

### Compute

| Service | Type | Description |
|---|---|---|
| EC2 | Virtual machines | Full control VMs, hundreds of instance types |
| Lambda | Serverless functions | Run code without servers, pay per invocation |
| ECS | Container service | Run Docker containers, AWS-native |
| EKS | Managed Kubernetes | Kubernetes control plane managed by AWS |

### Storage

| Service | Type | Best for |
|---|---|---|
| S3 | Object storage | Images, videos, backups, static websites — 11 nines durability |
| EBS | Block storage | EC2 attached persistent disk, databases |
| EFS | File storage | Shared access across multiple EC2 instances |
| Glacier | Archive | Long-term archival, very cheap, slow retrieval |

### Networking

| Service | Description |
|---|---|
| VPC | Your private isolated network in AWS |
| ELB | Load balancer — ALB (HTTP), NLB (TCP) |
| CloudFront | CDN — delivers content from 450+ edge locations |
| Direct Connect | Dedicated private physical line from office to AWS |

### Databases

| Service | Type | Best for |
|---|---|---|
| RDS | Relational SQL | Traditional apps, MySQL/PostgreSQL/SQL Server |
| Aurora | High-performance SQL | 5x faster MySQL, auto-scaling storage up to 128TB |
| DynamoDB | NoSQL key-value | Serverless, single-digit ms at any scale |
| Redshift | Data warehouse | Petabyte analytics, BI reports, columnar storage |

---

## 12. AWS IAM

### Core Components

**Users** — represent individual people or applications. Have long-term credentials.

**Groups** — collections of users. Attach policies to groups, not individual users.

**Roles** — temporary identities assumed by services (EC2, Lambda) or for cross-account access. Always prefer roles over long-term access keys.

**Policies** — JSON documents defining permissions. Evaluated on every API request.

### IAM Policy Structure

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "HumanReadableLabel",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-bucket/*"
    }
  ]
}
```

| Field | Required | Description |
|---|---|---|
| `Version` | Yes | Always `"2012-10-17"` — the policy language version, never changes |
| `Statement` | Yes | Array of one or more permission rules |
| `Sid` | No | Human-readable label for the rule, ignored by AWS |
| `Effect` | Yes | `"Allow"` or `"Deny"`. Explicit Deny always wins. |
| `Principal` | Yes (bucket policies) | Who the rule applies to. `"*"` = everyone |
| `Action` | Yes | Which AWS API operations. e.g. `s3:GetObject` |
| `Resource` | Yes | Which AWS resources. Uses ARN format |

### Why `"Version": "2012-10-17"`?

AWS has released two versions of their policy language syntax:
- `2008-10-17` — old version, very limited features
- `2012-10-17` — current version, always use this

The date is fixed forever — it refers to October 17, 2012 when AWS released the updated syntax. You always write this exact string in every policy you create.

### ARN Format

```
arn:aws:service:region:account-id:resource

arn:aws:s3:::my-bucket/*
         ↑  ↑↑  ↑
         s3  empty (S3 is global)  bucket-name/*
```

### IAM Best Practices

1. Enable MFA on root and all privileged accounts
2. Never use root account for daily work
3. Apply principle of least privilege
4. Use roles for services, not access keys
5. Rotate access keys regularly
6. Use IAM groups to manage permissions at scale

### MFA Types

| Type | Example |
|---|---|
| Virtual MFA | Google Authenticator app |
| Hardware key fob | Physical device from AWS |
| U2F security key | USB YubiKey |

---

## 13. AWS Resource Management

### CloudFormation

Infrastructure as Code (IaC) — define your entire AWS infrastructure in YAML or JSON templates. CloudFormation creates, updates, and deletes resources automatically.

```yaml
Resources:
  MyBucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: my-app-bucket
      VersioningConfiguration:
        Status: Enabled
```

- Version control your infrastructure like code
- Resources are grouped into **Stacks**
- Supports drift detection (finds manual changes)

### AWS Config

Continuously records and evaluates AWS resource configurations. Did someone open port 22 to the internet? Config detects it.

- Define compliance rules
- View configuration history timeline
- Get notified when resources drift from compliant state

### AWS Systems Manager

Manage EC2 instances at scale without SSH.

| Feature | Purpose |
|---|---|
| Run Command | Execute commands across hundreds of instances |
| Parameter Store | Securely store secrets and config values |
| Patch Manager | Automate OS patching |
| Session Manager | Secure browser-based terminal — no SSH keys needed |

### AWS Organizations

Manage multiple AWS accounts centrally.

- Group accounts into **Organizational Units (OUs)**
- Apply **Service Control Policies (SCPs)** to restrict what accounts can do
- Consolidated billing across all accounts
- Best practice: separate accounts per environment (dev, staging, production)

---

## 14. AWS Monitoring Tools

| Tool | Monitors | Key question answered |
|---|---|---|
| CloudWatch | Performance metrics and logs | Is my system healthy right now? |
| CloudTrail | Every API call ever made | Who did what in my account? |
| X-Ray | Request traces across services | Where is my app slow or failing? |
| Trusted Advisor | Account-wide best practices | How can I improve my setup? |
| Health Dashboard | AWS service disruptions | Is AWS having issues affecting me? |

### CloudWatch

Central monitoring service. Collects metrics from all AWS services (CPU, memory, requests). Set **alarms** to trigger actions when metrics breach thresholds.

- **Metrics** — numeric data points (CPU%, request count)
- **Logs** — application and service log files
- **Alarms** — fire when a metric crosses a threshold
- **Dashboards** — visual charts of your metrics

### CloudTrail

Records every API call in your AWS account — who, what, when, from where. Essential for security auditing and compliance.

- Enabled by default for 90 days
- Store long-term in S3
- Integrates with CloudWatch for real-time alerts on suspicious activity

### AWS X-Ray

Distributed tracing — follows a request as it travels through Lambda, API Gateway, DynamoDB, EC2. Shows where bottlenecks and errors occur in microservice architectures.

### Trusted Advisor

Automated checks across five pillars:
1. Cost optimisation
2. Performance
3. Security
4. Fault tolerance
5. Service limits

---

## 15. AWS Pricing and Support

### Pricing Models

| Model | Commitment | Discount | Best for |
|---|---|---|---|
| On-Demand | None | None (full price) | Unpredictable workloads, dev/test |
| Reserved Instances | 1 or 3 years | Up to 72% | Predictable steady workloads |
| Spot Instances | None (can be terminated) | Up to 90% | Fault-tolerant batch jobs, flexible workloads |
| Savings Plans | 1 or 3 years ($/hour) | Up to 66% | Flexible commitment across EC2, Lambda, Fargate |

### Cost Management Tools

- **Cost Explorer** — visualise and analyse spending over time
- **AWS Budgets** — set alerts when spending approaches a limit
- **Cost Allocation Tags** — tag resources to track spending by project or team

### Support Plans

| Plan | Cost | Critical response | Key feature |
|---|---|---|---|
| Basic | Free | None | Documentation, forums |
| Developer | From $29/month | 12–24 hours | Email support |
| Business | From $100/month | 1 hour | 24/7 phone, full Trusted Advisor |
| Enterprise | From $15,000/month | 15 minutes | Dedicated TAM, concierge |

---

## 16. AWS Security and Compliance

### Key Security Services

| Service | Purpose |
|---|---|
| KMS | Create and manage encryption keys for all AWS services |
| WAF | Web Application Firewall — blocks SQL injection, XSS, bad bots |
| Shield Standard | Free automatic DDoS protection |
| Shield Advanced | Enhanced DDoS protection with 24/7 response team |
| Inspector | Automated vulnerability scanning of EC2 and container images |
| GuardDuty | ML-based threat detection using CloudTrail, VPC flow logs, DNS |

### AWS Security Checklist

- [ ] Enable MFA on root and all privileged accounts
- [ ] Never use root account for daily tasks
- [ ] Apply least privilege to all IAM policies
- [ ] Enable CloudTrail in all regions
- [ ] Enable GuardDuty
- [ ] Encrypt data at rest (KMS) and in transit (TLS)
- [ ] Use VPC with private subnets for databases
- [ ] Regularly rotate access keys
- [ ] Enable AWS Config for compliance monitoring
- [ ] Use Security Hub for centralised security findings

### Compliance Certifications

AWS holds certifications for: SOC 1/2/3, ISO 27001, PCI DSS Level 1, HIPAA eligible services, GDPR compliance tools.

---

## 17. AWS DevOps and Automation

### CI/CD Pipeline on AWS

```
Developer pushes code
        ↓
CodePipeline detects commit → starts pipeline
        ↓
CodeBuild pulls code, runs tests, compiles, packages artifact
        ↓
Artifact stored in S3
        ↓
CodeDeploy deploys to EC2 / Lambda / ECS
(using Blue/Green or Rolling strategy)
        ↓
CloudWatch monitors deployment
        ↓
If errors spike → CodeDeploy auto-rolls back
        ↓
Developers notified via SNS
```

### DevOps Tools

| AWS Tool | Equivalent | Purpose |
|---|---|---|
| CodePipeline | GitHub Actions (orchestration) | Chain CI/CD stages together |
| CodeBuild | Jenkins build runner | Compile, test, package code |
| CodeDeploy | Octopus Deploy | Safe deployment with rollback |
| CloudFormation | Terraform (AWS-only) | Provision infrastructure as code |
| Elastic Beanstalk | Heroku | Deploy apps without managing infrastructure |
| Step Functions | Apache Airflow | Orchestrate multi-step serverless workflows |

### Deployment Strategies (CodeDeploy)

| Strategy | How it works | Risk |
|---|---|---|
| In-place (Rolling) | Update servers one by one | Medium — some old, some new during deploy |
| Blue/Green | Create new environment, switch traffic | Low — instant rollback possible |
| Canary | Send 5% traffic to new version first | Lowest — catch issues before full rollout |

### Terraform vs CloudFormation

| | CloudFormation | Terraform |
|---|---|---|
| Vendor | AWS only | Multi-cloud (AWS, Azure, GCP) |
| Language | YAML or JSON | HCL (HashiCorp Configuration Language) |
| State management | Managed by AWS | State file (local or remote) |
| Best for | AWS-only projects | Multi-cloud or team already using Terraform |

---

## 18. How Cloud Storage Works Internally

### How Google Photos Detects New Photos

When you install Google Photos, it registers as a background service with the OS:

**Android:** ContentObserver monitors the MediaStore database. Any new photo triggers an event that wakes Google Photos.

**iOS:** PHPhotoLibraryChangeObserver fires when the camera roll changes.

The app then adds the photo to an upload queue and waits for conditions to be met (WiFi connected, battery above 20%, phone not in heavy use). Uses **Resumable Upload** protocol — if the connection drops midway, upload resumes from the exact byte it stopped at.

### How Billions of Files Are Tracked

Every uploaded file becomes an object with:
- A unique ID
- A metadata record in a distributed database (Google Spanner)
- The actual binary stored in object storage
- A reference linking the user account → unique ID → storage location

**Google Spanner** handles billions of rows across thousands of machines acting as one database — globally consistent reads and writes across all data centers simultaneously.

### How Photos Are Compressed

Google uses **DCT (Discrete Cosine Transform)** compression:

1. Decode original JPEG back to raw pixels
2. Analyse content — complex areas keep more data, plain areas compress heavily
3. Apply DCT — converts pixel blocks to frequency data, reducing high-frequency detail
4. Re-encode at ~85% quality

```
12MP phone photo:
  Original:    4.2 MB
  Compressed:  1.8 MB
  Quality:     ~97% (imperceptible difference)
  Saved:       57%

108MP camera photo:
  Original:    25 MB
  Compressed:  3.5 MB (downsampled to 16MP limit)
  Saved:       86%
```

### Data Replication

Every file is stored at least 3 times across multiple geographic data centers. If one data center has an outage, the other copies remain accessible. This achieves 99.999999999% (11 nines) durability.

---

## 19. AWS IAM Policy Syntax Explained

### Full Breakdown of Every Field

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadAccess",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-bucket/*"
    }
  ]
}
```

#### `Version: "2012-10-17"`

The AWS policy language version. Always this exact string — it refers to October 17, 2012 when AWS updated the syntax. It never changes. There are only two valid values:
- `"2008-10-17"` — old, missing features, avoid
- `"2012-10-17"` — current, always use this

#### `Statement: [...]`

An array of permission rules. One policy can have multiple statements.

#### `Sid`

Statement ID. A human-readable label for the rule. Optional. AWS ignores it during evaluation. No spaces allowed. Used only for documentation purposes.

#### `Effect`

Two possible values only:
- `"Allow"` — grant the permission
- `"Deny"` — block the permission

> **Rule:** Explicit Deny always wins over Allow, even if 10 other policies allow it.

#### `Principal`

Who the rule applies to.

```json
"Principal": "*"                                          // everyone
"Principal": { "AWS": "arn:aws:iam::123456789:user/john" } // specific user
"Principal": { "Service": "lambda.amazonaws.com" }         // Lambda service
"Principal": { "AWS": "arn:aws:iam::123456789:role/name" } // specific role
```

#### `Action`

Which AWS API operations are covered. Format: `service:OperationName`

```
s3:GetObject      — download a file
s3:PutObject      — upload a file
s3:DeleteObject   — delete a file
s3:ListBucket     — list files in bucket
s3:*              — all S3 operations (wildcard)
```

Multiple actions:
```json
"Action": ["s3:GetObject", "s3:PutObject"]
```

#### `Resource`

Which specific AWS resources the rule applies to. Uses ARN format.

```
arn:aws:s3:::my-bucket        — the bucket itself
arn:aws:s3:::my-bucket/*      — all files in the bucket
arn:aws:s3:::my-bucket/img/*  — only files in the img/ folder
```

ARN format breakdown:
```
arn : aws : s3 : (region) : (account) : my-bucket/*
 ↑     ↑     ↑       ↑           ↑
fixed fixed service empty for S3  empty for S3
```

#### Reading it as one sentence

> Allow (`Effect`) everyone (`Principal: *`) to download files (`Action: s3:GetObject`) from any file in this bucket (`Resource: arn:...:my-bucket/*`).

---

## Quick Reference

### Cloud Terminology Cheatsheet

| Term | Short definition |
|---|---|
| Cloud computing | Using someone else's computers over the internet |
| IaaS | Rent raw VMs — you manage the OS upward |
| PaaS | Deploy code only — platform handles everything else |
| SaaS | Use finished apps — provider manages everything |
| Scalability | Ability to handle more load by adding resources |
| Elasticity | Automatically scaling up and down in real time |
| High Availability | Always on, minimal downtime via redundancy |
| Disaster Recovery | Plan to recover from catastrophic failure |
| RPO | How much data loss is acceptable (backup frequency) |
| RTO | How long the system can be down (recovery time target) |
| VPC | Your private network inside a cloud provider |
| IAM | Controls who can access what in your cloud account |
| GUID | Globally Unique Identifier — a random ID unique across the entire world |
| CDN | Content Delivery Network — serve files from nearest server to user |
| ORM | Object Relational Mapper — translates between C# objects and SQL tables |
| DI | Dependency Injection — classes receive dependencies rather than creating them |
| JWT | JSON Web Token — encrypted token proving who you are |
| CI/CD | Continuous Integration/Continuous Deployment — automated build-test-deploy pipeline |

---

*Notes compiled from cloud computing fundamentals through AWS L1 coursework.*
