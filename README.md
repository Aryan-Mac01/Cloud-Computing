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

### Advanced AWS Topics

20. [Advanced Compute](#1-advanced-compute)
21. [Advanced Networking](#2-advanced-networking)
22. [Advanced Storage](#3-advanced-storage)
23. [Advanced Databases](#4-advanced-databases)
24. [Advanced Identity and Security](#5-advanced-identity-and-security)
25. [Advanced Monitoring and Management](#6-advanced-monitoring-and-management)
26. [Advanced Governance and Compliance](#7-advanced-governance-and-compliance)
27. [AI and Machine Learning on AWS](#8-ai-and-machine-learning-on-aws)
28. [Big Data and Analytics](#9-big-data-and-analytics)
29. [Advanced Integration Services](#10-advanced-integration-services)
30. [AWS Pricing and Support](#11-aws-pricing-and-support)
31. [AWS Security and Compliance](#12-aws-security-and-compliance)
32. [AWS DevOps](#13-aws-devops)
33. [Terraform](#14-terraform)
34. [Backup and Disaster Recovery](#15-backup-and-disaster-recovery)

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


# AWS Advanced Topics — Complete Notes
 
> Advanced AWS services, administration, AI/ML, DevOps, compliance, and disaster recovery.
 
---
 
## Table of Contents
 
1. [Advanced Compute](#1-advanced-compute)
2. [Advanced Networking](#2-advanced-networking)
3. [Advanced Storage](#3-advanced-storage)
4. [Advanced Databases](#4-advanced-databases)
5. [Advanced Identity and Security](#5-advanced-identity-and-security)
6. [Advanced Monitoring and Management](#6-advanced-monitoring-and-management)
7. [Advanced Governance and Compliance](#7-advanced-governance-and-compliance)
8. [AI and Machine Learning on AWS](#8-ai-and-machine-learning-on-aws)
9. [Big Data and Analytics](#9-big-data-and-analytics)
10. [Advanced Integration Services](#10-advanced-integration-services)
11. [AWS Pricing and Support](#11-aws-pricing-and-support)
12. [AWS Security and Compliance](#12-aws-security-and-compliance)
13. [AWS DevOps](#13-aws-devops)
14. [Terraform](#14-terraform)
15. [Backup and Disaster Recovery](#15-backup-and-disaster-recovery)
 
---
 
## 1. Advanced Compute
 
### EC2 — Deep Dive
 
EC2 (Elastic Compute Cloud) is the core compute service. At an advanced level you need to understand instance families, purchasing options, placement, and auto scaling in depth.
 
#### EC2 Instance Families
 
Each family is optimised for a different workload type:
 
| Family | Optimised for | Example types | Use case |
|---|---|---|---|
| General Purpose | Balance of compute, memory, network | t3, t4g, m6i, m7g | Web servers, small databases |
| Compute Optimised | High CPU performance | c6i, c7g | Batch processing, gaming, scientific modelling |
| Memory Optimised | Large in-memory datasets | r6i, x2idn, u-6tb1 | In-memory databases, SAP HANA, Redis |
| Storage Optimised | High sequential read/write to local storage | i3, d3, h1 | Data warehousing, distributed file systems |
| Accelerated Computing | GPU / hardware accelerators | p4, g5, inf2 | ML training, video rendering, HPC |
| HPC Optimised | High performance computing | hpc6a | Computational fluid dynamics, genomics |
 
#### EC2 Purchasing Options
 
| Option | Commitment | Discount | Best for |
|---|---|---|---|
| On-Demand | None | None | Short-term, unpredictable workloads |
| Reserved Instances | 1 or 3 years | Up to 72% | Steady-state production workloads |
| Spot Instances | None (interruptible) | Up to 90% | Fault-tolerant batch, big data |
| Savings Plans | 1 or 3 years ($/hr spend) | Up to 66% | Flexible commitment across EC2, Lambda, Fargate |
| Dedicated Hosts | 1 or 3 years | Varies | Compliance, BYOL (Bring Your Own License) |
| Dedicated Instances | Per-instance | Some | Single-tenant hardware without full host control |
 
#### EC2 Placement Groups
 
Control how AWS physically places your EC2 instances:
 
| Type | How it works | Use case |
|---|---|---|
| Cluster | All instances in same rack, same AZ | Ultra-low latency HPC, tightly coupled apps |
| Spread | Each instance on different hardware | Critical apps needing maximum fault tolerance |
| Partition | Groups of instances on separate hardware partitions | Hadoop, Cassandra, Kafka — distributed systems |
 
#### Auto Scaling
 
Automatically adjust the number of EC2 instances based on demand.
 
**Components:**
- **Launch Template** — defines what instance to launch (AMI, instance type, security group, key pair)
- **Auto Scaling Group (ASG)** — defines min, max, and desired instance count
- **Scaling Policies** — rules for when to scale
 
**Scaling Policy Types:**
 
| Policy | How it triggers | Example |
|---|---|---|
| Target Tracking | Keep a metric at a target value | Keep average CPU at 50% |
| Step Scaling | Scale in steps based on alarm breach | CPU > 70% → add 2; CPU > 90% → add 5 |
| Scheduled Scaling | Scale at a specific time | Scale up every Monday 9 AM, scale down 6 PM |
| Predictive Scaling | ML forecast future load, scale proactively | Traffic always spikes at noon — pre-scale at 11:45 AM |
 
**Cooldown Period** — time after a scaling action where no new scaling happens. Prevents rapid thrashing up and down. Default 300 seconds.
 
#### EC2 Image Builder
 
Automates creation, maintenance, validation, and distribution of EC2 AMIs (Amazon Machine Images). Instead of manually configuring instances and creating snapshots, you define a pipeline:
 
```
Define recipe (base AMI + software + config)
        ↓
Build pipeline creates EC2 instance
        ↓
Installs software, applies patches
        ↓
Runs tests
        ↓
Creates new AMI
        ↓
Distributes to chosen regions
        ↓
Old AMIs deprecated automatically
```
 
### AWS Lambda — Advanced
 
#### Execution Model
 
Lambda runs your code in isolated execution environments (micro-VMs using Firecracker). Each invocation may reuse an existing warm environment or start a fresh one (cold start).
 
**Cold start** — first invocation after a period of inactivity. Container must be initialised. Adds 100ms–1s latency. Mitigated by:
- Provisioned Concurrency (pre-warm environments, costs money)
- Keeping functions small and dependencies minimal
- Using Lambda SnapStart (for Java)
 
**Warm start** — reuses an existing initialised environment. Near-instant. Code outside the handler function (global variables, database connections) persists between warm invocations.
 
#### Lambda Limits
 
| Limit | Value |
|---|---|
| Max execution timeout | 15 minutes |
| Max memory | 10,240 MB (10 GB) |
| Max deployment package size | 50 MB (zipped), 250 MB (unzipped) |
| Max ephemeral storage (/tmp) | 10 GB |
| Max concurrent executions (default) | 1,000 per region (can increase) |
| Max payload (synchronous) | 6 MB |
| Max payload (asynchronous) | 256 KB |
 
#### Lambda Triggers (Event Sources)
 
Lambda can be triggered by 30+ AWS services:
 
```
API Gateway      → HTTP request arrives
S3               → file uploaded / deleted
DynamoDB Streams → table row changed
SQS              → message in queue
SNS              → notification published
EventBridge      → scheduled cron or event rule
Kinesis          → streaming data record
Cognito          → user pool event (login, signup)
ALB              → load balancer request
CloudFront       → Lambda@Edge for CDN customisation
```
 
#### Lambda Destinations
 
For asynchronous invocations, route success/failure to different destinations:
 
```
Lambda function
├── On Success → SQS queue / SNS topic / EventBridge / another Lambda
└── On Failure → SQS queue / SNS topic / EventBridge / another Lambda
```
 
### AWS ECS — Advanced
 
**Elastic Container Service** runs Docker containers without managing container orchestration infrastructure.
 
#### Launch Types
 
| Launch Type | You manage | AWS manages | Cost model |
|---|---|---|---|
| EC2 | EC2 instances, scaling | Container scheduling | Pay for EC2 instances |
| Fargate | Nothing | Everything (serverless containers) | Pay per vCPU and memory used |
 
#### Key Concepts
 
- **Task Definition** — blueprint for your container (image, CPU, memory, ports, env vars, IAM role)
- **Task** — a running instance of a task definition (like a running container)
- **Service** — ensures a specified number of tasks are always running, handles replacements
- **Cluster** — logical grouping of tasks and services
 
#### ECS vs EKS
 
| | ECS | EKS |
|---|---|---|
| Orchestration | AWS-native | Kubernetes |
| Learning curve | Lower | Higher (need Kubernetes knowledge) |
| Vendor lock-in | AWS only | Portable across clouds |
| Community | AWS ecosystem | Large open-source community |
| Best for | AWS-first teams | Kubernetes-experienced teams, multi-cloud |
 
### AWS Batch
 
Run large-scale batch computing jobs without managing servers. Automatically provisions EC2 or Spot instances, runs your jobs, and terminates instances when done.
 
- **Job** — unit of work (a Docker container or shell script)
- **Job Queue** — jobs wait here until resources are available
- **Compute Environment** — the EC2 fleet that runs your jobs (managed or unmanaged)
 
Best for: genomics, financial modelling, video transcoding, scientific simulations.
 
### AWS Outposts
 
Brings AWS infrastructure (servers, networking) physically into your on-premises data center. You get the same AWS APIs, services, and tools but running locally. Useful for:
- Ultra-low latency requirements
- Data residency regulations
- Local data processing before sending to cloud
 
### AWS Wavelength
 
Deploys AWS compute and storage at the edge of 5G networks. Reduces latency to milliseconds for mobile and connected device applications. Used for real-time gaming, AR/VR, autonomous vehicles.
 
---
 
## 2. Advanced Networking
 
### VPC — Deep Dive
 
#### VPC CIDR Blocks
 
A VPC is defined by a CIDR block — a range of IP addresses.
 
```
10.0.0.0/16  →  65,536 available IP addresses
10.0.0.0/24  →  256 available IP addresses
10.0.1.0/24  →  256 available IP addresses (a subnet)
```
 
Rules:
- VPC CIDR must be between /16 (largest) and /28 (smallest)
- Subnets carve up the VPC CIDR into smaller ranges
- AWS reserves 5 IPs in every subnet (first 4 + last 1)
- Subnets in the same VPC cannot have overlapping CIDR blocks
 
#### VPC Components
 
| Component | Purpose |
|---|---|
| Internet Gateway (IGW) | Allows public subnet resources to reach the internet |
| NAT Gateway | Allows private subnet resources to reach the internet (outbound only) |
| Route Table | Defines where traffic goes. Each subnet has one route table. |
| Security Group | Stateful firewall at the instance/ENI level. Rules are allow-only. |
| Network ACL (NACL) | Stateless firewall at the subnet level. Supports allow and deny rules. |
| VPC Endpoint | Private connection to AWS services without internet |
| VPC Peering | Private connection between two VPCs |
| Transit Gateway | Hub connecting many VPCs and on-premises networks |
 
#### Security Groups vs Network ACLs
 
| Feature | Security Group | Network ACL |
|---|---|---|
| Level | Instance / ENI | Subnet |
| State | Stateful (return traffic auto-allowed) | Stateless (must allow inbound AND outbound) |
| Rules | Allow only | Allow and Deny |
| Rule evaluation | All rules evaluated | Rules evaluated in number order, first match wins |
| Default | Deny all inbound, allow all outbound | Allow all inbound and outbound |
 
#### NAT Gateway vs NAT Instance
 
| | NAT Gateway | NAT Instance |
|---|---|---|
| Managed by | AWS | You |
| Availability | Highly available within AZ | Single point of failure |
| Bandwidth | Up to 100 Gbps (auto-scales) | Depends on instance type |
| Cost | Higher | Lower (but you manage it) |
| Recommendation | Always prefer for production | Only if cost is critical concern |
 
#### VPC Peering
 
Connect two VPCs privately. Traffic never traverses the public internet.
 
- Can peer VPCs across different accounts and regions
- Not transitive — if A peers B and B peers C, A cannot reach C through B
- No overlapping CIDR blocks allowed
- No bandwidth bottleneck
 
#### Transit Gateway
 
A central hub that connects multiple VPCs and on-premises networks. Solves the non-transitive problem of VPC peering.
 
```
Without Transit Gateway (VPC Peering — non-transitive):
  VPC-A ←→ VPC-B
  VPC-B ←→ VPC-C
  VPC-A CANNOT reach VPC-C
 
With Transit Gateway:
  VPC-A ──┐
  VPC-B ──┤──→ Transit Gateway ──→ On-premises
  VPC-C ──┘
  Everyone can reach everyone
```
 
#### VPC Endpoints
 
Access AWS services privately without leaving the AWS network (no internet, no NAT gateway needed).
 
| Type | Works for | How |
|---|---|---|
| Gateway Endpoint | S3 and DynamoDB only | Added to route table, free |
| Interface Endpoint | Most other AWS services | Creates an ENI with private IP, costs money |
| PrivateLink | Your own services or third-party SaaS | Expose service privately to other VPCs |
 
### AWS Direct Connect
 
Dedicated private physical network connection from your data center to AWS. Bypasses the public internet entirely.
 
**Benefits:**
- Consistent, predictable bandwidth (1 Gbps or 10 Gbps)
- Lower latency than VPN
- Reduced data transfer costs for high-volume transfers
- Required for some compliance scenarios
 
**Direct Connect vs VPN:**
 
| | Direct Connect | Site-to-Site VPN |
|---|---|---|
| Connection | Physical dedicated line | Encrypted tunnel over internet |
| Latency | Very low, consistent | Higher, variable |
| Bandwidth | Up to 100 Gbps | Up to ~1.25 Gbps |
| Setup time | Weeks to months | Minutes |
| Cost | Higher | Lower |
| Reliability | SLA-backed | Depends on internet |
 
### AWS Route 53
 
Managed DNS service. Routes internet traffic to the right resources.
 
#### Routing Policies
 
| Policy | How it works | Use case |
|---|---|---|
| Simple | Returns one record (or random if multiple) | Single resource |
| Weighted | Split traffic by percentage | A/B testing, gradual migration |
| Latency | Route to lowest-latency region | Global apps with users in multiple regions |
| Failover | Primary normally, secondary if health check fails | High availability with DR |
| Geolocation | Route based on user's country/continent | Compliance, localisation |
| Geoproximity | Route based on geographic distance (bias adjustable) | Fine-grained geographic routing |
| Multi-value | Return multiple healthy records, client picks one | Simple load balancing at DNS level |
 
#### Health Checks
 
Route 53 monitors endpoint health. Unhealthy endpoints are removed from DNS responses automatically. Can monitor:
- HTTP/HTTPS/TCP endpoints
- Other Route 53 health checks (calculated health checks)
- CloudWatch alarms
 
### AWS CloudFront — Advanced
 
#### Cache Behaviour
 
CloudFront caches responses from your origin. You configure:
- **TTL (Time To Live)** — how long to cache (default 24 hours)
- **Cache keys** — what request attributes determine a unique cached object (URL, headers, cookies, query strings)
- **Origin request policy** — what to forward to origin
 
#### CloudFront Functions vs Lambda@Edge
 
| | CloudFront Functions | Lambda@Edge |
|---|---|---|
| Runtime | JavaScript only | Node.js, Python |
| Execution location | 450+ edge locations | 13 regional edge locations |
| Max duration | 1ms | 30 seconds |
| Memory | 2 MB | 128 MB – 10 GB |
| Triggers | Viewer request/response only | All 4 events |
| Cost | Very cheap | More expensive |
| Use case | Simple URL rewrites, header manipulation | Complex auth, A/B testing |
 
#### Origin Types
 
- **S3 bucket** — static websites, media files
- **EC2 / ALB** — dynamic content from your application
- **Custom HTTP origin** — any HTTP server (on-premises, third-party)
- **Origin Group** — primary + failover origin for high availability
 
### AWS Global Accelerator
 
Routes traffic through AWS's private global network instead of the public internet. Uses anycast IP addresses — users always connect to the nearest AWS edge location which then routes internally to your endpoints.
 
**vs CloudFront:**
- CloudFront: caches content at edge (for static content)
- Global Accelerator: no caching, just faster routing (for dynamic content, gaming, IoT, TCP/UDP)
 
### Elastic Load Balancing — Advanced
 
#### ALB (Application Load Balancer) — Layer 7
 
- Routes based on URL path, host, HTTP headers, query strings
- Native support for HTTP/2, gRPC, WebSockets
- Can return fixed responses without forwarding to backend
- Supports authentication via Cognito or OIDC providers
 
**ALB Routing rules example:**
```
/api/*       → Target Group: API servers
/images/*    → Target Group: Media servers
/admin/*     → Target Group: Admin servers (requires auth)
default      → Target Group: Web servers
```
 
#### NLB (Network Load Balancer) — Layer 4
 
- Routes TCP, UDP, TLS traffic
- Handles millions of requests per second
- Static IP addresses (useful for whitelisting)
- Ultra-low latency
- Preserves source IP
 
#### GLB (Gateway Load Balancer) — Layer 3
 
- For deploying third-party network appliances (firewalls, intrusion detection)
- Traffic is inspected by appliances before reaching destination
- Transparent — source/destination IPs preserved
 
---
 
## 3. Advanced Storage
 
### S3 — Deep Dive
 
#### S3 Storage Classes
 
| Class | Availability | Min storage | Retrieval | Use case |
|---|---|---|---|---|
| S3 Standard | 99.99% | None | Instant | Frequently accessed data |
| S3 Intelligent-Tiering | 99.9% | None | Instant | Unknown or changing access patterns |
| S3 Standard-IA | 99.9% | 30 days | Instant | Infrequently accessed, rapid retrieval needed |
| S3 One Zone-IA | 99.5% | 30 days | Instant | Non-critical, reproducible data |
| S3 Glacier Instant | 99.9% | 90 days | Instant | Archive with instant access |
| S3 Glacier Flexible | 99.99% | 90 days | Minutes to hours | Archives, retrieval in 1-12 hours |
| S3 Glacier Deep Archive | 99.99% | 180 days | 12-48 hours | Regulatory archives, 7-10 year retention |
 
#### S3 Lifecycle Policies
 
Automatically transition objects between storage classes or delete them based on age:
 
```yaml
Rules:
  - Transition to Standard-IA after: 30 days
  - Transition to Glacier Flexible after: 90 days
  - Transition to Glacier Deep Archive after: 180 days
  - Expire (delete) objects after: 365 days
```
 
#### S3 Versioning
 
When enabled, S3 keeps all versions of an object. Deleting an object adds a delete marker — the previous versions still exist.
 
- Protects against accidental deletion
- Enables recovery of overwritten objects
- Costs money (every version is stored and billed)
- Once enabled, cannot be fully disabled (only suspended)
 
#### S3 Replication
 
| Type | Replicates to | Use case |
|---|---|---|
| CRR (Cross-Region Replication) | Different AWS region | Compliance, disaster recovery, lower latency |
| SRR (Same-Region Replication) | Same region, different bucket | Log aggregation, dev/prod sync |
 
Requirements: versioning must be enabled on both source and destination buckets.
 
#### S3 Event Notifications
 
Trigger actions when objects are created, deleted, or restored:
 
```
S3 Event → SQS queue
S3 Event → SNS topic
S3 Event → Lambda function
S3 Event → EventBridge (most flexible, filter rules)
```
 
#### S3 Security
 
**Bucket Policies** — resource-based policies attached to the bucket. Control access from any principal including other accounts and public internet.
 
**ACLs (Access Control Lists)** — legacy, per-object or per-bucket. AWS recommends disabling ACLs in favour of bucket policies.
 
**Block Public Access** — four settings that override any policy allowing public access. Should be on for almost all buckets.
 
**Pre-signed URLs** — temporary URLs that grant time-limited access to a specific private object. Generated programmatically. Expires after a set time (max 7 days via AWS SDK).
 
```
# Example: share a private file for 1 hour
aws s3 presign s3://my-private-bucket/report.pdf --expires-in 3600
```
 
**S3 Object Lock** — prevent objects from being deleted or overwritten for a defined retention period. Two modes:
- **Governance mode** — users with special permission can override
- **Compliance mode** — no one can override, including root account. Used for strict regulatory compliance.
 
#### S3 Performance
 
- **Multipart Upload** — split large files into parts, upload in parallel. Recommended for files > 100 MB, required for files > 5 GB.
- **S3 Transfer Acceleration** — uses CloudFront edge locations to accelerate uploads from distant locations.
- **S3 Select** — query only a subset of data in a CSV/JSON/Parquet file using SQL. Reduces data transferred and speeds up processing.
- **S3 Byte-Range Fetches** — download specific byte ranges of a file in parallel.
 
### EBS — Deep Dive
 
#### EBS Volume Types
 
| Type | Category | Max IOPS | Max throughput | Use case |
|---|---|---|---|---|
| gp3 | SSD | 16,000 | 1,000 MB/s | General purpose (default choice) |
| gp2 | SSD | 16,000 | 250 MB/s | Legacy general purpose |
| io2 Block Express | SSD | 256,000 | 4,000 MB/s | Critical databases (Oracle, SAP) |
| io1 | SSD | 64,000 | 1,000 MB/s | High-performance databases |
| st1 | HDD | 500 | 500 MB/s | Throughput-heavy (Kafka, log processing) |
| sc1 | HDD | 250 | 250 MB/s | Cold data, lowest cost HDD |
 
> **gp3 vs gp2:** gp3 is the newer standard. It decouples IOPS and throughput from volume size (you can set them independently). gp2 ties IOPS to size (3 IOPS per GB). gp3 is cheaper and more flexible — always prefer gp3.
 
#### EBS Snapshots
 
Point-in-time backups of EBS volumes stored in S3 (managed by AWS, you don't see the S3 bucket).
 
- Incremental — only changed blocks since last snapshot are saved
- Can copy snapshots across regions and accounts
- Can create AMIs from snapshots
- Can restore into a new EBS volume in any AZ
 
**Amazon Data Lifecycle Manager (DLM)** — automates EBS snapshot creation and deletion. Define policies like "snapshot every day at midnight, keep last 7 snapshots."
 
#### EBS Multi-Attach
 
Allows a single io1/io2 EBS volume to be attached to multiple EC2 instances simultaneously (up to 16 instances) in the same AZ. Used for clustered databases that manage concurrent writes themselves (Oracle RAC).
 
### AWS Storage Gateway
 
Connects on-premises environments to cloud storage. A virtual appliance (VM) or hardware appliance running in your data center that presents cloud storage as local storage.
 
| Gateway Type | Presents as | Backed by | Use case |
|---|---|---|---|
| S3 File Gateway | NFS/SMB file share | S3 | File shares backed by S3 |
| FSx File Gateway | SMB file share | FSx for Windows | Windows file shares with local cache |
| Volume Gateway (Cached) | iSCSI block device | S3 (primary) + local cache | Low-latency access to frequently used data |
| Volume Gateway (Stored) | iSCSI block device | Local (primary) + S3 backup | Full dataset on-premises, backup to S3 |
| Tape Gateway | Virtual tape library | S3 Glacier | Replace physical tape backup systems |
 
### AWS FSx
 
Fully managed third-party file systems:
 
| Service | Compatible with | Use case |
|---|---|---|
| FSx for Windows File Server | SMB, Windows | Windows workloads, Active Directory integration |
| FSx for Lustre | Lustre (Linux HPC) | HPC, ML training, video processing, fast S3 integration |
| FSx for NetApp ONTAP | NFS, SMB, iSCSI | Multi-protocol enterprise storage |
| FSx for OpenZFS | NFS | Linux workloads needing ZFS features (snapshots, clones) |
 
### AWS Transfer Family
 
Managed file transfer service supporting SFTP, FTPS, and FTP directly into and out of S3 or EFS. No server infrastructure to manage. Used for migrating legacy file transfer workflows to cloud storage.
 
---
 
## 4. Advanced Databases
 
### RDS — Deep Dive
 
#### Multi-AZ Deployment
 
AWS automatically provisions and maintains a synchronous standby replica in a different AZ.
 
```
Primary RDS (AZ-1a)  ──sync replication──→  Standby RDS (AZ-1b)
 
Normal operation: all traffic goes to primary
If primary fails:  automatic failover to standby (60-120 seconds)
DNS endpoint: always points to current primary — app reconnects automatically
```
 
- Standby is NOT a read replica — it is idle until failover
- Provides HA, not performance improvement
- Automatic backups taken from standby (no I/O impact on primary)
 
#### Read Replicas
 
Asynchronous copies of the primary database for offloading read traffic.
 
- Up to 15 read replicas per RDS instance (Aurora)
- Can be in same AZ, different AZ, or different region
- Applications must be coded to send reads to replica endpoint
- Can be promoted to standalone database (DR scenario)
- Cross-region read replicas for disaster recovery
 
#### RDS Proxy
 
A fully managed database proxy that sits between your application and RDS. Pools and shares database connections.
 
**Why it matters:** Lambda functions can create thousands of concurrent connections, overwhelming RDS. RDS Proxy maintains a connection pool and multiplexes thousands of Lambda connections into a few database connections.
 
```
Without RDS Proxy:
  1000 Lambda invocations → 1000 database connections → RDS overwhelmed
 
With RDS Proxy:
  1000 Lambda invocations → RDS Proxy → 10 pooled connections → RDS stable
```
 
#### RDS Automated Backups and Snapshots
 
| | Automated Backups | Manual Snapshots |
|---|---|---|
| Triggered by | AWS automatically | You manually |
| Retention | 0-35 days | Until you delete |
| Point-in-time recovery | Yes (to any second in retention window) | No (snapshot point only) |
| Stored in | S3 (managed by AWS) | S3 (managed by AWS) |
| Deleted with instance | Yes | No |
 
#### RDS Parameter Groups and Option Groups
 
- **Parameter Group** — configuration settings for the database engine (e.g. max connections, query cache size)
- **Option Group** — enable optional features (e.g. Oracle's native audit, SQL Server's transparent data encryption)
 
### Aurora — Deep Dive
 
Aurora is AWS's custom-built relational database. MySQL and PostgreSQL compatible but engineered from scratch for cloud performance and availability.
 
#### Aurora Architecture
 
```
Writer Instance (Primary)
        ↓ writes
Shared Distributed Storage (6 copies across 3 AZs, 10 GB chunks)
        ↑ reads
Reader Instances (up to 15 read replicas)
```
 
Key differences from standard RDS:
- Storage is decoupled from compute — auto-scales from 10 GB to 128 TB
- 6 copies of data across 3 AZs automatically — no manual Multi-AZ setup
- Failover to read replica takes ~30 seconds (vs 60-120 seconds for standard RDS)
- Parallel query — push analytical query processing down to storage layer
 
#### Aurora Serverless v2
 
Aurora with automatic compute scaling. Database scales from 0.5 to 128 ACUs (Aurora Capacity Units) in fine-grained increments within seconds.
 
- Pay only for capacity used
- Scales up instantly on traffic spike, scales down to near-zero when idle
- Perfect for variable/unpredictable workloads, dev/test environments
- Supports all Aurora features including Multi-AZ and global database
 
#### Aurora Global Database
 
One Aurora cluster spans multiple AWS regions:
 
```
Primary Region (ap-south-1)  ──→  Secondary Region (us-east-1)
Write here                         Read from here
                                   Failover destination (<1 second lag)
```
 
- Replication lag: typically < 1 second
- Up to 5 secondary regions
- Managed failover — promote secondary region to primary in < 1 minute
 
#### Aurora Machine Learning
 
Directly call AWS ML services (SageMaker, Comprehend) from SQL queries:
 
```sql
SELECT product_name,
       aws_comprehend_detect_sentiment(review_text, 'en') AS sentiment
FROM product_reviews;
```
 
### DynamoDB — Deep Dive
 
#### DynamoDB Data Model
 
DynamoDB is a key-value and document database. Every item must have a primary key.
 
**Primary Key types:**
- **Partition Key only (Simple PK)** — single attribute that must be unique. DynamoDB hashes it to determine which partition stores the item.
- **Partition Key + Sort Key (Composite PK)** — combination must be unique. Items with same partition key are stored together, sorted by sort key. Enables range queries.
 
```
Table: Orders
Partition Key: CustomerId
Sort Key: OrderDate
 
CustomerId  OrderDate    Total
─────────────────────────────
user123     2025-01-05   $45
user123     2025-02-12   $120   ← same partition key, different sort key
user456     2025-01-08   $67
```
 
#### DynamoDB Indexes
 
| Index Type | Key | Purpose |
|---|---|---|
| Local Secondary Index (LSI) | Same partition key, different sort key | Alternative sort order on same partition |
| Global Secondary Index (GSI) | Different partition key and sort key | Query by non-primary-key attributes |
 
LSIs must be created at table creation. GSIs can be added anytime. Up to 5 of each.
 
#### Read/Write Capacity Modes
 
| Mode | How you pay | When to use |
|---|---|---|
| Provisioned | Specify RCUs and WCUs upfront | Predictable, consistent traffic |
| On-Demand | Pay per request | Spiky, unpredictable traffic |
 
**RCU (Read Capacity Unit):** 1 strongly consistent read per second for items up to 4 KB
**WCU (Write Capacity Unit):** 1 write per second for items up to 1 KB
 
#### DynamoDB Streams
 
A time-ordered sequence of every change made to a DynamoDB table. Each record contains the before and after state of the item. Retained for 24 hours.
 
Common use: trigger Lambda on data changes (real-time replication, cache invalidation, notifications).
 
#### DynamoDB Accelerator (DAX)
 
In-memory cache for DynamoDB. Reduces read latency from milliseconds to microseconds.
 
```
App → DAX → DynamoDB
      ↑
      Cache hit: returns data in microseconds
      Cache miss: fetches from DynamoDB, caches result
```
 
- Write-through cache — writes go to both DAX and DynamoDB
- API-compatible — no application code changes needed (just change endpoint)
- Not useful for: write-heavy workloads, strongly consistent reads, rarely-read items
 
#### DynamoDB Global Tables
 
Multi-region, multi-active replication. Any region can accept reads and writes. AWS automatically replicates changes across all regions using last-writer-wins reconciliation.
 
```
ap-south-1  ←──────→  us-east-1  ←──────→  eu-west-1
Write here              Write here             Write here
Read here               Read here              Read here
All changes replicate to all regions
```
 
### Amazon ElastiCache
 
Managed in-memory caching. Two engines:
 
#### Redis vs Memcached
 
| Feature | Redis | Memcached |
|---|---|---|
| Data structures | Strings, lists, sets, hashes, sorted sets, streams | Strings only |
| Persistence | Yes (AOF and RDB) | No |
| Replication | Yes (primary + replicas) | No |
| Multi-AZ failover | Yes | No |
| Pub/Sub | Yes | No |
| Cluster mode | Yes | Yes |
| Use case | Sessions, leaderboards, queues, ML features | Simple key-value caching |
 
**Recommendation:** Use Redis for almost all use cases. Memcached only if you need maximum simplicity and don't need persistence.
 
#### Caching Strategies
 
| Strategy | How | Trade-off |
|---|---|---|
| Lazy Loading (Cache-aside) | Read from cache; on miss, read from DB and populate cache | Stale data possible; only caches what's actually needed |
| Write Through | Write to DB and cache simultaneously | Cache always fresh; writes slightly slower |
| Write Behind | Write to cache first, async write to DB later | Fastest writes; risk of data loss |
| TTL | Set expiry on cache keys | Simple freshness control |
 
### Amazon Redshift — Deep Dive
 
Petabyte-scale data warehouse. Uses columnar storage and massively parallel processing (MPP).
 
#### Why Columnar Storage?
 
```
Row-based (MySQL, PostgreSQL):
  Stores: [id, name, price, category], [id, name, price, category]...
  Query: "SUM of all prices" → reads ALL columns for ALL rows
 
Columnar (Redshift):
  Stores: all prices together, all names together...
  Query: "SUM of all prices" → reads ONLY the price column
  Result: 10-100x faster for analytical queries
```
 
#### Redshift Architecture
 
- **Leader node** — receives queries, plans execution, coordinates
- **Compute nodes** — execute the query in parallel, store data in slices
- **Node slices** — each compute node divided into slices, each processing a portion of data
 
#### Redshift Spectrum
 
Query data directly in S3 from Redshift without loading it first. Enables a data lake architecture where raw data stays in S3 and Redshift queries it alongside warehouse data.
 
#### Redshift Serverless
 
Automatically provisions and scales Redshift capacity based on workload. No cluster management needed. Pay per compute-second used.
 
---
 
## 5. Advanced Identity and Security
 
### AWS IAM — Advanced
 
#### IAM Permission Boundaries
 
A permission boundary is a managed policy that sets the maximum permissions an IAM entity can have. Even if the entity has a policy granting full admin access, the boundary limits what they can actually do.
 
```
User policy: Allow s3:*, ec2:*, rds:*
Permission boundary: Allow s3:* only
Effective permissions: s3:* only (boundary wins)
```
 
Used to: delegate permission management to developers safely — they can create IAM roles but cannot grant themselves more permissions than defined in the boundary.
 
#### IAM Policy Evaluation Logic
 
When a request is made, AWS evaluates policies in this order:
 
```
1. Explicit Deny in any policy? → DENY (stops here)
2. SCPs (Org Service Control Policies) allow it?  → If no, DENY
3. Resource-based policy allows it? → ALLOW (for same account)
4. IAM permission boundary allows it? → If no, DENY
5. Session policy allows it? → If no, DENY
6. Identity-based policy allows it? → If yes, ALLOW; if no, DENY
```
 
#### Cross-Account Access with IAM Roles
 
Allow users from Account A to access resources in Account B:
 
```
Account A user → AssumeRole → Account B Role → Account B resources
 
Account B: create role with trust policy allowing Account A:
{
  "Principal": { "AWS": "arn:aws:iam::ACCOUNT_A_ID:root" }
}
 
Account A user: aws sts assume-role --role-arn arn:aws:iam::ACCOUNT_B_ID:role/CrossAccountRole
Returns: temporary credentials (Access Key, Secret, Session Token)
```
 
#### AWS STS — Security Token Service
 
Issues temporary security credentials. Used by:
- IAM roles (AssumeRole)
- Identity federation (web identity, SAML)
- AWS services assuming roles
 
Temporary credentials expire (15 minutes to 36 hours). More secure than long-term access keys.
 
### AWS Cognito
 
User identity management for web and mobile applications.
 
#### Cognito User Pools
 
A user directory for your application. Handles:
- Sign up and sign in
- Password policies and MFA
- Social login (Google, Facebook, Apple)
- Email/SMS verification
- JWT tokens issued after authentication (ID token, Access token, Refresh token)
 
#### Cognito Identity Pools (Federated Identities)
 
Exchange any identity token (User Pool token, social login, SAML) for temporary AWS credentials. Allows authenticated and unauthenticated (guest) access to AWS services directly.
 
```
User logs in → User Pool issues JWT
JWT → Identity Pool → STS AssumeRoleWithWebIdentity
STS returns → temporary AWS credentials
App uses credentials → directly access S3, DynamoDB etc.
```
 
#### User Pools vs Identity Pools
 
| | User Pools | Identity Pools |
|---|---|---|
| Purpose | Authentication (who are you?) | Authorisation (what AWS can you access?) |
| Output | JWT tokens | Temporary AWS credentials |
| Used for | App login, user management | Granting AWS resource access to users |
 
### AWS Directory Service
 
Managed Microsoft Active Directory in AWS.
 
| Option | Description | Use case |
|---|---|---|
| AWS Managed Microsoft AD | Full AD in AWS, join EC2 instances to domain | Large enterprises needing full AD |
| AD Connector | Proxy — redirects requests to on-premises AD | Keep existing on-premises AD, no user sync |
| Simple AD | Lightweight AD-compatible (Samba 4) | Small orgs, basic AD features only |
 
### AWS Secrets Manager
 
Centrally store, rotate, and retrieve secrets (database passwords, API keys, OAuth tokens).
 
**Key features:**
- Automatic rotation of secrets (e.g. RDS password every 30 days, no app downtime)
- Encryption at rest using KMS
- Fine-grained access control via IAM
- Audit via CloudTrail
- Cross-account secret sharing
 
```python
# Retrieve secret in application code
import boto3
client = boto3.client('secretsmanager')
secret = client.get_secret_value(SecretId='prod/myapp/database')
```
 
**vs Parameter Store:**
 
| | Secrets Manager | SSM Parameter Store |
|---|---|---|
| Cost | $0.40/secret/month | Free (standard), small fee for advanced |
| Auto rotation | Yes, built-in | No (custom Lambda needed) |
| Cross-account | Yes | Yes |
| Best for | Passwords, API keys needing rotation | Config values, feature flags |
 
### AWS Certificate Manager (ACM)
 
Provision, manage, and deploy SSL/TLS certificates for AWS services (ALB, CloudFront, API Gateway).
 
- Public certificates: free, automatically renewed by AWS
- Private certificates: for internal services (paid)
- Cannot export public certificates (private key stays with ACM)
 
### AWS KMS — Advanced
 
#### Key Types
 
| Type | Who creates key material | Rotation | Control |
|---|---|---|---|
| AWS Managed Keys | AWS | Automatic (annual) | Limited |
| Customer Managed Keys (CMK) | You (or AWS) | Optional (annual) | Full |
| Customer Provided Keys (SSE-C) | You | You manage | Full, not stored in AWS |
 
#### Envelope Encryption
 
KMS never encrypts large data directly. It uses envelope encryption:
 
```
1. You request a data key from KMS
2. KMS returns: plaintext data key + encrypted data key
3. You encrypt your data using the plaintext data key
4. Store: encrypted data + encrypted data key (together)
5. Discard plaintext data key (never store it)
 
To decrypt:
1. Send encrypted data key to KMS
2. KMS decrypts it using your CMK → returns plaintext data key
3. Use plaintext data key to decrypt your data
```
 
This way your data never goes through KMS — only the small key does.
 
#### KMS Key Policies
 
KMS keys have their own resource-based policies (key policies). IAM policies alone are not enough — the key policy must also allow access.
 
### AWS WAF — Advanced
 
#### Web ACL Rules
 
Rules evaluate web requests and take action (Allow, Block, Count, CAPTCHA):
 
| Rule type | Example |
|---|---|
| IP Set match | Block requests from specific IPs |
| Geographic match | Block traffic from certain countries |
| SQL injection match | Block requests containing SQL injection patterns |
| Rate-based rule | Block IPs making more than 2000 requests in 5 minutes |
| Managed rule groups | Pre-built rules from AWS or marketplace (OWASP Top 10) |
| Custom rule | Combine conditions with AND/OR/NOT logic |
 
#### WAF Logging
 
Send all web request logs to:
- CloudWatch Logs
- S3 bucket
- Kinesis Data Firehose
 
Enables analysis of traffic patterns, blocked request investigation, compliance auditing.
 
---
 
## 6. Advanced Monitoring and Management
 
### Amazon CloudWatch — Advanced
 
#### CloudWatch Metrics
 
Every AWS service publishes metrics to CloudWatch automatically. You can also publish custom application metrics.
 
```python
# Publish custom metric from application
import boto3
cloudwatch = boto3.client('cloudwatch')
cloudwatch.put_metric_data(
    Namespace='MyApp/Performance',
    MetricData=[{
        'MetricName': 'OrdersProcessed',
        'Value': 47,
        'Unit': 'Count'
    }]
)
```
 
**Metric resolution:**
- Standard: 1-minute granularity (default, free)
- High-resolution: 1-second granularity (custom metrics only, costs more)
 
#### CloudWatch Alarms — States
 
| State | Meaning |
|---|---|
| OK | Metric is within threshold |
| ALARM | Metric has breached threshold |
| INSUFFICIENT_DATA | Not enough data to determine state (startup, gaps) |
 
#### Composite Alarms
 
Combine multiple alarms with AND/OR logic. Only triggers if the condition across multiple alarms is met. Reduces alarm noise.
 
```
Composite Alarm: "ApplicationDown"
Condition: ALARMing CPU > 90% AND ALARMing Latency > 5s AND ALARMing ErrorRate > 10%
→ Only alerts when all three are true simultaneously
```
 
#### CloudWatch Logs Insights
 
Interactive query language for CloudWatch Logs. Query millions of log events in seconds.
 
```sql
fields @timestamp, @message
| filter @message like /ERROR/
| stats count(*) as errorCount by bin(5m)
| sort errorCount desc
| limit 20
```
 
#### CloudWatch Container Insights
 
Enhanced monitoring for EKS, ECS, and Kubernetes. Collects metrics and logs at cluster, node, pod, task, and service level. Provides pre-built dashboards.
 
#### CloudWatch Lambda Insights
 
Extension layer for Lambda that captures system-level metrics (CPU, memory, disk, network) alongside Lambda's own metrics (duration, errors, cold starts).
 
### AWS CloudTrail — Advanced
 
#### Trail Types
 
| Type | Coverage | Storage |
|---|---|---|
| Management events | API calls on AWS resources (default, free for first copy) | CloudTrail console, S3 |
| Data events | Object-level S3 operations, Lambda invocations (high volume, costs money) | S3 |
| Insights events | Unusual activity detection (spike in API calls) | S3 |
 
#### CloudTrail Lake
 
Query CloudTrail events using SQL across multiple accounts and regions. Events stored for up to 7 years. Faster than querying Athena on S3.
 
```sql
SELECT userIdentity.arn, eventName, eventTime
FROM myEventDataStore
WHERE eventName = 'DeleteBucket'
AND eventTime > '2025-01-01'
```
 
### AWS Config — Advanced
 
#### Config Rules
 
Evaluate AWS resource configurations against desired settings:
 
**AWS Managed Rules (pre-built):**
```
s3-bucket-public-read-prohibited   → S3 buckets must not allow public read
restricted-ssh                     → Security groups must not allow SSH from 0.0.0.0/0
rds-instance-public-access-check   → RDS must not be publicly accessible
mfa-enabled-for-iam-console-access → IAM users must have MFA enabled
```
 
**Custom Rules:** Write your own Lambda function to evaluate compliance.
 
**Remediation:** Automatically fix non-compliant resources using SSM Automation documents.
 
#### Config Aggregator
 
Aggregates compliance data across multiple accounts and regions into a single view. Uses AWS Organizations for automatic discovery of all accounts.
 
### AWS Systems Manager — Advanced
 
#### Session Manager
 
Browser-based or CLI terminal access to EC2 instances. No SSH, no port 22, no bastion host needed.
 
Benefits:
- No inbound security group rules needed
- All sessions logged to CloudWatch and S3
- Works through NAT — no public IP needed
- Supports Windows and Linux
 
#### SSM Parameter Store — Advanced
 
Hierarchical storage for configuration data and secrets:
 
```
/myapp/prod/database/host     → db.cluster.ap-south-1.rds.amazonaws.com
/myapp/prod/database/password → (SecureString, encrypted with KMS)
/myapp/prod/api/key          → (SecureString)
/myapp/dev/database/host     → dev-db.ap-south-1.rds.amazonaws.com
```
 
**Standard vs Advanced Parameters:**
- Standard: free, max 4 KB per parameter, 10,000 parameters
- Advanced: $0.05/parameter/month, max 8 KB, 100,000 parameters, parameter policies (TTL, notification on expiry)
 
#### SSM Automation
 
Run pre-defined runbooks (automation documents) on AWS resources. Can patch instances, create AMIs, start/stop instances on schedule, remediate Config findings.
 
#### AWS OpsWorks
 
Configuration management using Chef or Puppet. Manage instance configuration, application deployment, software installation across a fleet. Considered legacy — most teams use Systems Manager or Ansible instead.
 
---
 
## 7. Advanced Governance and Compliance
 
### AWS Organizations — Advanced
 
#### Organizational Units (OUs)
 
Hierarchical grouping of accounts:
 
```
Root
├── Management Account
├── OU: Infrastructure
│   ├── Networking Account
│   └── Security Account
├── OU: Workloads
│   ├── OU: Production
│   │   ├── Prod-App Account
│   │   └── Prod-Data Account
│   └── OU: Development
│       └── Dev Account
└── OU: Sandbox
    └── Experiment Account
```
 
#### Service Control Policies (SCPs)
 
JSON policies attached to OUs or accounts that restrict what services and actions can be used — even by administrators within those accounts.
 
SCPs do not grant permissions — they only restrict. An account still needs IAM policies to actually allow actions.
 
```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Deny",
    "Action": "*",
    "Resource": "*",
    "Condition": {
      "StringNotEquals": {
        "aws:RequestedRegion": ["ap-south-1", "us-east-1"]
      }
    }
  }]
}
```
This SCP blocks all actions in any region except Mumbai and N. Virginia — even if a user has AdminAccess.
 
#### AWS Control Tower
 
Landing zone automation — sets up a multi-account AWS environment following AWS best practices. Creates:
- Management account structure
- Log archive account (centralized CloudTrail and Config)
- Audit account (for security tooling)
- Pre-configured guardrails (preventive SCPs + detective Config rules)
 
Best for: organisations starting fresh or standardising their AWS environment.
 
### AWS Service Catalog
 
Create and manage catalogues of approved IT services. Developers can deploy pre-approved, compliant resources without needing broad IAM permissions.
 
```
Admin creates Product (CloudFormation template for approved VPC)
Admin creates Portfolio (collection of products)
Admin grants Portfolio access to developers
 
Developer → Service Catalog → picks approved VPC product → launches it
Developer never sees the CloudFormation template
Developer cannot modify it
All deployments are compliant by design
```
 
### AWS License Manager
 
Track software licences across AWS and on-premises. Enforce licence rules to prevent overuse. Supported for: Windows Server, SQL Server, Oracle, SAP, and more.
 
### AWS Trusted Advisor — Advanced
 
#### Five Pillars of Checks
 
| Pillar | Example checks |
|---|---|
| Cost Optimisation | Underutilised EC2 instances, idle RDS, low-utilisation EBS |
| Performance | CloudFront header forwarding, EC2 overloaded instances |
| Security | Open S3 buckets, MFA not on root, exposed access keys |
| Fault Tolerance | Multi-AZ not enabled on RDS, single AZ Auto Scaling Groups |
| Service Limits | Approaching VPC limits, EC2 limits |
 
Full access requires Business or Enterprise support plan.
 
### AWS Well-Architected Framework
 
Five pillars for designing cloud architectures:
 
| Pillar | Key principle |
|---|---|
| Operational Excellence | Run and monitor systems, continuously improve processes |
| Security | Protect data, systems, and assets through risk assessment and mitigation |
| Reliability | Recover from disruptions, dynamically acquire resources |
| Performance Efficiency | Use compute resources efficiently, maintain that efficiency as demand changes |
| Cost Optimisation | Avoid unnecessary costs, understand spending and control allocation |
 
**AWS Well-Architected Tool** — review your workload against the framework, get improvement recommendations.
 
---
 
## 8. AI and Machine Learning on AWS
 
### Amazon SageMaker
 
End-to-end machine learning platform. Covers every stage of the ML lifecycle:
 
```
Data preparation → Model training → Model evaluation → Model deployment → Monitoring
```
 
#### SageMaker Components
 
| Component | Purpose |
|---|---|
| SageMaker Studio | Integrated IDE for ML (Jupyter-based) |
| SageMaker Data Wrangler | Visual data preparation and feature engineering |
| SageMaker Feature Store | Centralised repository of ML features |
| SageMaker Training | Managed training jobs on any instance type |
| SageMaker Experiments | Track, compare, and evaluate ML experiments |
| SageMaker Debugger | Real-time monitoring of training jobs |
| SageMaker Model Registry | Version and manage trained models |
| SageMaker Endpoints | Deploy models as real-time REST APIs |
| SageMaker Batch Transform | Offline predictions on large datasets |
| SageMaker Pipelines | CI/CD for ML workflows |
| SageMaker Clarify | Detect bias in data and models, explain predictions |
| SageMaker Canvas | No-code ML for business users |
 
#### SageMaker Training
 
```
1. Specify training data location (S3)
2. Choose algorithm (built-in or custom)
3. Choose instance type (CPU ml.m5.xlarge, GPU ml.p3.2xlarge)
4. Set hyperparameters
5. SageMaker provisions instance, downloads data, runs training, saves model to S3
6. Instance terminated after training completes — pay only while training
```
 
**Built-in algorithms:** XGBoost, Linear Learner, K-Means, Random Cut Forest, Image Classification, Object Detection, BlazingText, DeepAR (time series).
 
### AWS Pre-Built AI Services
 
Use AI without building or training models. Call via API.
 
| Service | What it does | Example use |
|---|---|---|
| Rekognition | Image and video analysis | Face detection, object recognition, content moderation |
| Textract | Extract text and structured data from documents | Extract data from invoices, forms, PDFs |
| Comprehend | Natural language processing | Sentiment analysis, entity extraction, topic modelling |
| Translate | Neural machine translation | Real-time multilingual content |
| Polly | Text to speech | Voice apps, accessibility |
| Transcribe | Speech to text | Meeting transcription, call analytics |
| Lex | Conversational AI (chatbots) | Customer service chatbots (powers Alexa) |
| Forecast | Time series forecasting | Demand forecasting, inventory planning |
| Personalize | Real-time personalisation and recommendations | Product recommendations, content ranking |
| Fraud Detector | Online fraud detection | Account fraud, payment fraud |
| Kendra | Intelligent enterprise search | Search across documents, PDFs, wikis |
| Bedrock | Foundation models as API | Access Claude, Llama, Titan, Stable Diffusion |
 
### Amazon Bedrock
 
Access large foundation models (LLMs and image models) via API without managing infrastructure.
 
**Available model families:**
- **Anthropic Claude** — conversational AI, analysis, coding
- **Meta Llama** — open-source LLM
- **Amazon Titan** — AWS's own models (text, embeddings, image)
- **Stability AI** — image generation (Stable Diffusion)
- **Cohere** — text generation and embeddings
- **AI21 Jurassic** — text generation
 
**Bedrock features:**
- Knowledge Bases — connect models to your documents (RAG)
- Agents — models that can call APIs and take actions
- Fine-tuning — customise models on your data
- Model evaluation — compare model outputs
- Guardrails — content filtering and safety
 
### AWS AI Development Lifecycle (AI SDLC)
 
Building AI products requires a different lifecycle from regular software:
 
| Stage | Activity |
|---|---|
| Problem Definition | Is AI the right solution? What does success look like? |
| Data Collection | Gather training data from relevant sources |
| Data Preparation | Clean, label, balance, split (train/validation/test) |
| Model Selection | Choose algorithm type based on problem |
| Model Training | Feed data, optimise parameters |
| Model Evaluation | Measure accuracy, precision, recall, F1 score |
| Deployment | Serve as API endpoint (SageMaker Endpoints) |
| Monitoring | Track prediction quality over time, retrain when drift detected |
 
---
 
## 9. Big Data and Analytics
 
### AWS Analytics Stack
 
```
Data Sources → Ingestion → Storage → Processing → Analysis → Visualisation
     ↓              ↓          ↓           ↓            ↓           ↓
  Apps, DBs,    Kinesis,    S3 Data    EMR,        Athena,     QuickSight,
  IoT, Logs     Glue ETL    Lake/      Spark,      Redshift,   Grafana
                            Redshift   Flink       OpenSearch
```
 
### Amazon Kinesis
 
Real-time data streaming platform. Four services:
 
#### Kinesis Data Streams
 
Collect and process streaming data in real time. Producers write records, consumers read and process them.
 
- Data retained 24 hours by default (up to 365 days)
- Ordered within a shard
- Multiple consumers can read the same stream independently
- Scale by adding shards (each shard: 1 MB/s write, 2 MB/s read)
 
```
IoT sensors → Kinesis Data Streams → Lambda (process) → DynamoDB (store)
                                   → Kinesis Analytics (analyse in real time)
                                   → Kinesis Firehose (archive to S3)
```
 
#### Kinesis Data Firehose
 
Capture, transform, and load streaming data into destinations. Fully managed — no shards to manage.
 
**Destinations:** S3, Redshift, OpenSearch, Splunk, HTTP endpoint, Datadog, New Relic
 
- Buffer data (by size up to 128 MB or time up to 900 seconds)
- Transform with Lambda before delivery
- Near-real-time (60 second minimum latency)
 
#### Kinesis Data Analytics
 
Run SQL or Apache Flink applications on streaming data in real time. No servers to manage.
 
```sql
-- Real-time anomaly detection
SELECT STREAM product_id, AVG(price) OVER (RANGE INTERVAL '1' MINUTE PRECEDING)
FROM product_stream
WHERE price > AVG(price) * 2
```
 
#### Kinesis Video Streams
 
Ingest, process, and store video streams from connected devices. Used for ML-based video analysis, playback, and archival.
 
### AWS Glue
 
Fully managed ETL (Extract, Transform, Load) service.
 
#### Glue Components
 
| Component | Purpose |
|---|---|
| Data Catalog | Centralised metadata repository — schemas, table definitions |
| Crawlers | Automatically scan data sources and populate the Catalog |
| ETL Jobs | Python or Scala Spark jobs to transform data |
| Glue Studio | Visual drag-and-drop ETL designer |
| Glue DataBrew | Visual data profiling and preparation (no code) |
| Triggers | Schedule or event-driven ETL job execution |
| Glue Streaming | Continuous ETL from Kinesis or Kafka |
 
**Common pattern:**
```
Raw data in S3
→ Glue Crawler scans it → creates table in Glue Catalog
→ Athena can now query it with SQL
→ Glue ETL job transforms and loads into Redshift
```
 
### Amazon Athena
 
Interactive SQL query service for data in S3. Serverless — no infrastructure. Pay per query ($5 per TB of data scanned).
 
- Supports CSV, JSON, Parquet, ORC, Avro
- Use Parquet or ORC format + partition data to massively reduce cost and improve speed
- Integrates with Glue Catalog for schema management
- Federated queries — query non-S3 sources (RDS, DynamoDB, on-premises via connector)
 
```sql
-- Query raw log files stored in S3
SELECT status_code, COUNT(*) as count
FROM access_logs
WHERE year='2025' AND month='03'
GROUP BY status_code
ORDER BY count DESC;
```
 
### Amazon EMR
 
Managed cluster platform for big data processing using open-source frameworks:
 
| Framework | Use case |
|---|---|
| Apache Spark | Fast distributed data processing, ML at scale |
| Apache Hadoop | Large-scale batch processing (HDFS + MapReduce) |
| Apache Hive | SQL-like queries on large datasets |
| Apache HBase | NoSQL on Hadoop |
| Presto | Interactive SQL on multiple data sources |
| Apache Flink | Real-time stream processing |
 
**EMR Serverless** — run Spark and Hive without managing clusters. AWS auto-provisions resources per job.
 
**EMR on EKS** — run EMR workloads on your existing EKS cluster.
 
### Amazon OpenSearch Service
 
Managed Elasticsearch/OpenSearch for search and log analytics.
 
Common use cases:
- Log analytics (centralise application logs, search and visualise)
- Full-text search for applications
- Security analytics (SIEM — aggregate security events)
- Real-time monitoring
 
Integrates with Kinesis Firehose for real-time log ingestion, CloudWatch for metrics.
 
### AWS Lake Formation
 
Build, secure, and manage data lakes on S3. Simplifies setting up a data lake from weeks to days.
 
- Ingests data from databases and S3
- Catalogues data using Glue
- Row and column level security on the data lake
- Fine-grained access control — grant access to specific tables and columns across Athena, Redshift Spectrum, EMR
 
### Amazon QuickSight
 
Cloud-native business intelligence and visualisation tool. Create dashboards and reports from data in S3, Athena, Redshift, RDS, and more.
 
**SPICE** — Super-fast Parallel In-memory Calculation Engine. Caches data in memory for sub-second query performance. Each user gets 10 GB free.
 
**ML Insights** — anomaly detection, forecasting, and natural language queries built in.
 
---
 
## 10. Advanced Integration Services
 
### Amazon SQS — Deep Dive
 
#### Queue Types
 
| Type | Ordering | Deduplication | Throughput | Use case |
|---|---|---|---|---|
| Standard | Best-effort (not guaranteed) | Best-effort | Unlimited | High throughput, order not critical |
| FIFO | Strict order guaranteed | Exactly-once | 3,000 msg/s (with batching) | Orders, financial transactions |
 
#### Key Settings
 
| Setting | Description |
|---|---|
| Visibility Timeout | Time a message is hidden after a consumer reads it. If not deleted in time, message reappears. Default: 30 seconds. |
| Message Retention | How long messages stay if not consumed. Default: 4 days. Max: 14 days. |
| Delay Queue | Postpone delivery of new messages. Up to 15 minutes. |
| Long Polling | Wait up to 20 seconds for messages. Reduces empty responses, saves cost. |
| Dead Letter Queue (DLQ) | Messages that fail processing N times are sent here for investigation. |
 
#### SQS as a Buffer
 
Classic pattern to decouple and protect downstream services:
 
```
Users → API Gateway → SQS → Lambda/EC2 (process at own pace)
                      ↑
                    Buffer
                    Handles traffic spikes
                    Downstream never overwhelmed
```
 
### Amazon SNS — Deep Dive
 
Pub/Sub messaging. Publishers send to a topic. All subscribers receive every message.
 
#### Subscription Types
 
| Protocol | Use case |
|---|---|
| SQS | Fan-out to multiple queues |
| Lambda | Trigger function per message |
| HTTP/HTTPS | Send to any webhook |
| Email | Send email notifications |
| SMS | Send text message to phone |
| Mobile Push | iOS (APNs), Android (FCM), Amazon ADM |
| Kinesis Firehose | Stream messages for archival/processing |
 
#### SNS Fan-Out Pattern
 
One event triggers multiple parallel processing paths:
 
```
S3 upload event → SNS topic
                  ├── SQS Queue A → Lambda → resize image
                  ├── SQS Queue B → Lambda → extract metadata
                  └── SQS Queue C → Lambda → update search index
```
 
#### SNS Message Filtering
 
Subscribers can filter which messages they receive using message attributes. Reduces unnecessary Lambda invocations and SQS messages.
 
```json
Filter policy: { "event_type": ["order_placed"] }
Only receive messages where event_type attribute = "order_placed"
```
 
### Amazon EventBridge
 
Serverless event bus. Route events between AWS services, your applications, and SaaS partners.
 
#### Event Buses
 
| Bus | Events |
|---|---|
| Default event bus | AWS service events (EC2 state change, RDS snapshot complete, etc.) |
| Custom event bus | Your application events |
| Partner event bus | SaaS events (Zendesk, Shopify, Datadog, GitHub) |
 
#### Rules
 
Match events and route them to targets:
 
```json
Event pattern (match EC2 instance stopping):
{
  "source": ["aws.ec2"],
  "detail-type": ["EC2 Instance State-change Notification"],
  "detail": { "state": ["stopping"] }
}
 
Targets: Lambda, SQS, SNS, Kinesis, Step Functions, API Gateway, another EventBridge
```
 
#### EventBridge Scheduler
 
Highly scalable cron and one-time schedule service. Replaces CloudWatch Events for scheduling. Supports millions of schedules.
 
```
Schedule: cron(0 2 * * ? *)     → Run every day at 2 AM UTC
Schedule: rate(5 minutes)        → Run every 5 minutes
One-time: 2025-12-25T00:00:00Z  → Run once on Christmas
```
 
### AWS Step Functions
 
Serverless workflow orchestration. Define multi-step workflows as state machines.
 
#### State Types
 
| State | Purpose |
|---|---|
| Task | Call a service (Lambda, ECS, SageMaker, DynamoDB, etc.) |
| Choice | Conditional branching (if/else) |
| Wait | Pause for a time period or timestamp |
| Parallel | Execute branches simultaneously |
| Map | Iterate over an array, process each item |
| Pass | Pass data through without doing work |
| Succeed / Fail | End the workflow |
 
#### Express vs Standard Workflows
 
| | Standard | Express |
|---|---|---|
| Duration | Up to 1 year | Up to 5 minutes |
| Execution model | Exactly-once | At-least-once |
| History | Full audit in console | CloudWatch Logs |
| Price | Per state transition | Per invocation + duration |
| Use case | Long-running business processes | High-volume, short-duration |
 
### Amazon MQ
 
Managed message broker for Apache ActiveMQ and RabbitMQ. Used when migrating existing on-premises applications that use standard messaging protocols (AMQP, MQTT, STOMP, OpenWire).
 
New applications should use SQS/SNS. MQ is specifically for legacy migrations.
 
### AWS AppSync
 
Managed GraphQL API service. Automatically generates a GraphQL API from your data sources (DynamoDB, Lambda, RDS, HTTP).
 
- Real-time subscriptions via WebSocket
- Offline data synchronisation for mobile apps
- Fine-grained authorisation (Cognito, API Key, IAM, Lambda)
 
### Amazon API Gateway — Advanced
 
#### API Types
 
| Type | Protocol | Use case |
|---|---|---|
| REST API | HTTP/REST | Feature-rich, request validation, caching |
| HTTP API | HTTP/REST | Simpler, cheaper, faster, OIDC/JWT auth built in |
| WebSocket API | WebSocket | Real-time bidirectional (chat, gaming, live dashboards) |
 
#### API Gateway Features
 
- **Throttling** — limit request rate per API key or globally (protect backend)
- **Usage Plans** — assign rate limits and quotas to API keys (for monetising APIs)
- **Caching** — cache responses at edge, reduce backend calls (0.5 GB to 237 GB)
- **Request/Response Transformation** — modify request before sending to backend, modify response before returning to client
- **Authorisers** — Lambda authoriser (custom logic), Cognito authoriser (JWT validation)
- **VPC Link** — access private resources (EC2, ECS) inside a VPC from API Gateway
 
---
 
## 11. AWS Pricing and Support
 
### Pricing Models — Deep Dive
 
#### On-Demand
 
Pay for compute by the hour or second (minimum 60 seconds for EC2). No long-term commitment. Most expensive per unit. Best for:
- Variable workloads you cannot predict
- Applications being developed or tested
- Short-duration workloads (< 1 year)
 
#### Reserved Instances
 
Commit to a specific instance type, region, and term (1 or 3 years). Three payment options:
 
| Payment | Discount | Cash flow |
|---|---|---|
| All Upfront | Highest (~72%) | Pay everything now |
| Partial Upfront | Medium (~60%) | Pay some now, rest monthly |
| No Upfront | Lower (~40%) | Pay monthly, no upfront cost |
 
**Convertible Reserved Instances** — can change instance family, OS, tenancy during the term. Lower discount (~54%) but more flexibility.
 
**Scheduled Reserved Instances** — reserve for specific time windows (e.g. batch job every weekday 6-10 PM). Deprecated — use Savings Plans or On-Demand now.
 
#### Spot Instances
 
AWS sells unused EC2 capacity at steep discount. AWS can reclaim with 2-minute warning.
 
**Spot Instance Interruption handling:**
- Always design for interruption tolerance
- Use Spot with Auto Scaling Groups (ASG handles replacement)
- Combine On-Demand (baseline) + Spot (burst) in ASG
- Use EC2 Spot Fleet or ECS Spot capacity providers
 
**Best workloads for Spot:**
- Big data processing (EMR)
- Batch jobs
- CI/CD build workers
- Stateless web servers
- Machine learning training (with checkpointing)
 
#### AWS Savings Plans
 
More flexible than Reserved Instances. Commit to a consistent amount of compute spend ($/hour) for 1 or 3 years.
 
| Type | Applies to | Discount |
|---|---|---|
| Compute Savings Plan | EC2 (any family, region, OS), Lambda, Fargate | Up to 66% |
| EC2 Instance Savings Plan | Specific instance family in a region | Up to 72% |
| SageMaker Savings Plan | SageMaker | Up to 64% |
 
### AWS Cost Management Tools
 
#### AWS Cost Explorer
 
- Visualise costs and usage over time
- Break down by service, account, tag, region, instance type
- Rightsizing recommendations (identifies over-provisioned EC2)
- Forecast costs for next 12 months
- Reserved Instance and Savings Plan recommendations
 
#### AWS Budgets
 
Set budget thresholds and receive alerts:
 
| Budget Type | Alert on |
|---|---|
| Cost budget | When spending exceeds threshold |
| Usage budget | When usage (e.g. EC2 hours) exceeds threshold |
| Reservation budget | RI utilisation drops below target |
| Savings Plans budget | Savings Plan coverage drops below target |
 
**Budgets Actions** — automatically apply an IAM policy or target an EC2/RDS action when a budget threshold is breached (e.g. stop EC2 instances if budget exceeded).
 
#### AWS Cost and Usage Report (CUR)
 
The most detailed billing data. Line-item data for every resource in every hour. Delivered to S3. Query with Athena or load into Redshift for custom cost analytics.
 
#### Cost Allocation Tags
 
Apply key-value tags to resources. Activate tags for cost allocation. AWS splits costs by tag in Cost Explorer and CUR.
 
```
Tags for a production web server:
  Environment: Production
  Project: GroceryStore
  Team: Backend
  CostCenter: Engineering
```
 
### AWS Support Plans
 
| Plan | Cost | Response (critical) | Key features |
|---|---|---|---|
| Basic | Free | No support | Documentation, forums, 7 Trusted Advisor checks |
| Developer | $29/month or 3% of usage | 12 hours (business hours) | Email support, one primary contact |
| Business | $100/month or 10% of usage | 1 hour | 24/7 phone/chat, full Trusted Advisor, Health API |
| Enterprise On-Ramp | $5,500/month | 30 minutes | Pool of TAMs, Concierge, Incident Detection |
| Enterprise | $15,000/month | 15 minutes | Dedicated TAM, proactive reviews, training credits |
 
**Technical Account Manager (TAM)** — dedicated AWS expert who knows your account, architecture, and business goals. Proactively helps with architectural reviews, operational planning, and incident response.
 
### Service Level Agreements (SLAs)
 
AWS guarantees uptime percentages for most services. If AWS fails to meet the SLA, you receive service credits.
 
| Service | Monthly Uptime SLA |
|---|---|
| EC2 | 99.99% |
| S3 | 99.9% |
| RDS Multi-AZ | 99.95% |
| DynamoDB | 99.99% |
| Lambda | 99.95% |
| CloudFront | 99.9% |
 
**SLA credit calculation:** More downtime = more credit percentage (up to 100% of monthly bill for the affected service).
 
---
 
## 12. AWS Security and Compliance
 
### AWS Compliance Programs
 
AWS maintains compliance certifications for the underlying infrastructure. Your applications may also need to be compliant — that is your responsibility.
 
| Standard | Description | Common in |
|---|---|---|
| SOC 1/2/3 | Service Organisation Controls — financial and security reporting | Financial services |
| ISO 27001 | Information security management | Global |
| ISO 27017 | Cloud security controls | Cloud services |
| ISO 27018 | Protection of PII in cloud | GDPR regions |
| PCI DSS Level 1 | Payment card industry data security | Payments |
| HIPAA | Health Insurance Portability and Accountability Act | Healthcare (USA) |
| FedRAMP | Federal Risk and Authorization Management Program | US government |
| GDPR | General Data Protection Regulation | EU/UK |
| SOC 2 Type II | Security, availability, confidentiality over time | SaaS |
 
**AWS Artifact** — self-service portal to download AWS compliance reports and certifications.
 
### AWS Security Hub
 
Centralised security findings aggregator across your AWS account and across multiple accounts.
 
- Ingests findings from: GuardDuty, Inspector, Macie, IAM Access Analyzer, Firewall Manager, Partner solutions
- Scores your security posture against standards (AWS Foundational Security Best Practices, CIS Benchmarks, PCI DSS)
- Prioritises findings by severity
- Automated response workflows via EventBridge
 
### Amazon Macie
 
ML-powered sensitive data discovery and data privacy service for S3.
 
- Discovers PII (names, credit cards, passport numbers, bank accounts) in S3
- Identifies buckets with public access, unencrypted data, shared outside account
- Generates findings sent to Security Hub and EventBridge
- Used for GDPR, HIPAA, PCI compliance
 
### Amazon Inspector
 
Automated vulnerability assessment:
 
- **EC2:** scans packages for CVEs, checks network exposure
- **ECR (Container Images):** scans container images on push and continuously
- **Lambda:** scans function code and layers for vulnerabilities
 
Assigns a risk score (0-10) to each finding. Integrates with Security Hub.
 
### AWS Firewall Manager
 
Centrally manage WAF rules, Shield Advanced, security groups, and Network Firewall policies across all accounts in your AWS Organisation.
 
- Define security policies once, apply automatically to all accounts
- New accounts automatically get the policies on creation
- No need to configure WAF separately on each account
 
### AWS Network Firewall
 
Managed stateful network firewall for VPCs. Inspects traffic flowing between subnets, from internet, to internet.
 
- Stateful packet inspection
- Intrusion prevention system (IPS)
- URL/domain filtering (block specific domains)
- Operates at network layer (unlike WAF which operates at HTTP layer)
 
### Data Protection
 
#### Encryption at Rest
 
Every AWS storage service supports encryption at rest:
 
| Service | Encryption option |
|---|---|
| S3 | SSE-S3 (AWS managed), SSE-KMS (your KMS key), SSE-C (your key) |
| EBS | AES-256, encrypted at volume level using KMS |
| RDS | Encrypted at creation using KMS (cannot enable after creation) |
| DynamoDB | AES-256, always encrypted, KMS for customer-managed keys |
| EFS | KMS-based encryption at creation |
 
#### Encryption in Transit
 
- All AWS API calls use HTTPS (TLS 1.2+)
- RDS supports TLS connections
- S3 can require HTTPS via bucket policy (`aws:SecureTransport` condition)
- ELB terminates SSL/TLS (offloads from backend instances)
 
---
 
## 13. AWS DevOps
 
### AWS CodePipeline — Advanced
 
Full CI/CD orchestration service. A pipeline consists of stages, each containing actions.
 
#### Pipeline Structure
 
```
Source Stage → Build Stage → Test Stage → Deploy Stage
    ↓               ↓             ↓             ↓
 CodeCommit      CodeBuild     CodeBuild     CodeDeploy
 GitHub          Runs unit     Runs          or
 S3 zip          tests         integration   Elastic Beanstalk
                               tests         or ECS
```
 
#### Action Types
 
| Category | Actions |
|---|---|
| Source | CodeCommit, GitHub, GitLab, Bitbucket, S3, ECR |
| Build | CodeBuild, Jenkins |
| Test | CodeBuild, Device Farm, third-party (Blazemeter) |
| Deploy | CodeDeploy, Beanstalk, ECS, CloudFormation, S3, Service Catalog |
| Approval | Manual approval gate (human must approve before pipeline continues) |
| Invoke | Lambda function |
 
### AWS CodeBuild — Advanced
 
Managed build service. Defined entirely by `buildspec.yml` in your repository root.
 
#### buildspec.yml Structure
 
```yaml
version: 0.2
 
env:
  variables:
    NODE_ENV: production
  parameter-store:
    DB_PASSWORD: /myapp/prod/database/password
 
phases:
  install:
    runtime-versions:
      nodejs: 20
    commands:
      - npm install
 
  pre_build:
    commands:
      - echo Logging in to ECR
      - aws ecr get-login-password | docker login --username AWS --password-stdin $ECR_URL
 
  build:
    commands:
      - npm test
      - npm run build
      - docker build -t myapp:$CODEBUILD_RESOLVED_SOURCE_VERSION .
      - docker push $ECR_URL/myapp:$CODEBUILD_RESOLVED_SOURCE_VERSION
 
  post_build:
    commands:
      - echo Build completed successfully
 
artifacts:
  files:
    - '**/*'
  base-directory: dist
 
cache:
  paths:
    - node_modules/**/*
```
 
### AWS CodeDeploy — Advanced
 
#### Deployment Configurations
 
**In-Place (Rolling):**
```
EC2 fleet: [A] [B] [C] [D]
 
Step 1: stop A, deploy new version → [A'] [B] [C] [D]
Step 2: stop B, deploy            → [A'] [B'] [C] [D]
Step 3: stop C, deploy            → [A'] [B'] [C'] [D]
Step 4: stop D, deploy            → [A'] [B'] [C'] [D']
```
 
**Blue/Green:**
```
Blue (current):  [A] [B] [C] [D]  ← production traffic
Green (new):     [A'] [B'] [C'] [D']  ← new version
 
Test green
Switch load balancer → green now receives all traffic
Blue kept for rollback window, then terminated
```
 
**Canary (for Lambda/ECS):**
```
Canary10Percent5Minutes:
  0-5 minutes: 10% traffic → new version, 90% → old
  After 5 minutes: if no errors → 100% → new version
  If errors: automatic rollback to 100% old version
```
 
#### AppSpec File
 
Defines what CodeDeploy does during deployment:
 
```yaml
# For EC2
version: 0.0
os: linux
files:
  - source: /build
    destination: /var/www/myapp
 
hooks:
  BeforeInstall:
    - location: scripts/stop_server.sh
      timeout: 300
  AfterInstall:
    - location: scripts/install_dependencies.sh
  ApplicationStart:
    - location: scripts/start_server.sh
  ValidateService:
    - location: scripts/health_check.sh
      timeout: 60
```
 
### GitHub Actions for AWS
 
Common patterns for AWS deployments via GitHub Actions:
 
```yaml
name: Deploy to AWS
 
on:
  push:
    branches: [main]
 
jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      id-token: write   # required for OIDC
      contents: read
 
    steps:
      - uses: actions/checkout@v4
 
      - name: Configure AWS credentials (OIDC — no access keys stored)
        uses: aws-actions/configure-aws-credentials@v4
        with:
          role-to-assume: arn:aws:iam::123456789:role/GitHubActionsRole
          aws-region: ap-south-1
 
      - name: Login to ECR
        uses: aws-actions/amazon-ecr-login@v2
 
      - name: Build and push Docker image
        run: |
          docker build -t $ECR_URL/myapp:${{ github.sha }} .
          docker push $ECR_URL/myapp:${{ github.sha }}
 
      - name: Deploy to ECS
        uses: aws-actions/amazon-ecs-deploy-task-definition@v1
        with:
          task-definition: task-definition.json
          service: myapp-service
          cluster: myapp-cluster
```
 
**OIDC vs Access Keys:** Use OIDC (the `id-token: write` permission above) to avoid storing AWS access keys as GitHub secrets. GitHub gets a short-lived token that can assume an IAM role. More secure.
 
### AWS Elastic Beanstalk — Advanced
 
#### Deployment Policies
 
| Policy | How it works | Downtime | Rollback speed |
|---|---|---|---|
| All at once | Deploy to all instances simultaneously | Yes (brief) | Manual |
| Rolling | Deploy in batches | No (partial capacity) | Manual |
| Rolling with additional batch | Add extra instances during deploy, then remove | No (full capacity) | Manual |
| Immutable | Deploy to new instances, swap when healthy | No | Fast (terminate new) |
| Blue/Green | Deploy to separate environment, CNAME swap | No | Instant (CNAME swap back) |
| Traffic splitting | Canary deployment — split traffic % | No | Very fast |
 
**Recommendation for production:** Immutable or Blue/Green. Rolling risks having mixed versions during deployment.
 
#### Beanstalk Configuration Files (.ebextensions)
 
Customise your Beanstalk environment using YAML/JSON config files in a `.ebextensions/` folder in your deployment package:
 
```yaml
# .ebextensions/nginx.config
files:
  "/etc/nginx/conf.d/proxy.conf":
    mode: "000644"
    owner: root
    group: root
    content: |
      client_max_body_size 20M;
 
container_commands:
  01_migrate:
    command: "python manage.py migrate"
    leader_only: true
```
 
---
 
## 14. Terraform
 
### What is Terraform?
 
Terraform is an open-source Infrastructure as Code (IaC) tool by HashiCorp. Write human-readable configuration files that describe your desired infrastructure, and Terraform creates, updates, and destroys resources to match.
 
Works with 300+ providers: AWS, Azure, GCP, Kubernetes, GitHub, Datadog, and more.
 
### Terraform vs CloudFormation
 
| Feature | Terraform | CloudFormation |
|---|---|---|
| Cloud support | Multi-cloud | AWS only |
| Language | HCL (HashiCorp Configuration Language) | YAML or JSON |
| State management | State file (local or remote in S3) | Managed by AWS |
| Provider ecosystem | 300+ providers | AWS + some partners |
| Plan/preview | `terraform plan` shows exact changes | Change sets |
| Rollback | Manual (re-apply previous config) | Automatic |
| Modules | Terraform Registry, any Git repo | Nested stacks, Service Catalog |
| Learning curve | Medium | Medium |
 
### Core Terraform Concepts
 
#### Providers
 
Plugins that know how to talk to a specific API. Must be declared and installed.
 
```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}
 
provider "aws" {
  region = "ap-south-1"
}
```
 
#### Resources
 
The infrastructure objects you want to create.
 
```hcl
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
 
  tags = {
    Name        = "main-vpc"
    Environment = "production"
  }
}
 
resource "aws_subnet" "public" {
  vpc_id            = aws_vpc.main.id   # reference to above resource
  cidr_block        = "10.0.1.0/24"
  availability_zone = "ap-south-1a"
 
  tags = {
    Name = "public-subnet"
  }
}
```
 
#### Variables
 
Input parameters for reusability:
 
```hcl
variable "environment" {
  description = "Deployment environment"
  type        = string
  default     = "development"
}
 
variable "instance_type" {
  description = "EC2 instance type"
  type        = string
}
 
# Use in resource:
resource "aws_instance" "web" {
  instance_type = var.instance_type
  tags = {
    Environment = var.environment
  }
}
```
 
Pass values via `terraform.tfvars`:
```hcl
environment   = "production"
instance_type = "t3.micro"
```
 
#### Outputs
 
Export values from your Terraform configuration (e.g. to use in other modules or display after apply):
 
```hcl
output "vpc_id" {
  description = "ID of the created VPC"
  value       = aws_vpc.main.id
}
 
output "public_subnet_id" {
  value = aws_subnet.public.id
}
```
 
#### Data Sources
 
Read information about existing resources not managed by your Terraform:
 
```hcl
data "aws_ami" "amazon_linux" {
  most_recent = true
  owners      = ["amazon"]
 
  filter {
    name   = "name"
    values = ["amzn2-ami-hvm-*-x86_64-gp2"]
  }
}
 
resource "aws_instance" "web" {
  ami           = data.aws_ami.amazon_linux.id
  instance_type = "t3.micro"
}
```
 
#### State File
 
Terraform records what it created in a state file (`terraform.tfstate`). It compares current state against desired state on each plan/apply.
 
**Remote state in S3** (best practice for teams):
 
```hcl
terraform {
  backend "s3" {
    bucket         = "my-terraform-state-bucket"
    key            = "production/terraform.tfstate"
    region         = "ap-south-1"
    encrypt        = true
    dynamodb_table = "terraform-state-lock"  # prevents concurrent applies
  }
}
```
 
### Terraform Workflow
 
```bash
# 1. Initialise — download providers, set up backend
terraform init
 
# 2. Format — auto-format code to standard style
terraform fmt
 
# 3. Validate — check syntax
terraform validate
 
# 4. Plan — preview changes (dry run)
terraform plan
 
# 5. Apply — create/update/destroy resources
terraform apply
 
# 6. Destroy — tear down all resources
terraform destroy
```
 
### Terraform Modules
 
Reusable, composable units of Terraform configuration.
 
```hcl
# Using a module
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "5.0.0"
 
  name = "my-vpc"
  cidr = "10.0.0.0/16"
 
  azs             = ["ap-south-1a", "ap-south-1b"]
  private_subnets = ["10.0.1.0/24", "10.0.2.0/24"]
  public_subnets  = ["10.0.4.0/24", "10.0.5.0/24"]
 
  enable_nat_gateway = true
}
```
 
### Terraform in CI/CD
 
```yaml
# GitHub Actions Terraform pipeline
- name: Terraform Plan
  run: |
    terraform init
    terraform plan -out=tfplan
 
- name: Terraform Apply (main branch only)
  if: github.ref == 'refs/heads/main'
  run: terraform apply tfplan
```
 
**Atlantis** — open-source tool that runs Terraform via GitHub pull request comments. Reviewers see the plan output as a PR comment before approving.
 
**Terraform Cloud / HCP Terraform** — HashiCorp's managed platform for Terraform runs, state management, policy enforcement, and team collaboration.
 
---
 
## 15. Backup and Disaster Recovery
 
### Disaster Recovery Strategies
 
Four strategies, ordered by cost and recovery speed:
 
#### 1. Backup and Restore (Cheapest, Slowest)
 
Back up data to S3. Restore to new infrastructure when disaster strikes.
 
```
Normal: production infrastructure running
Disaster: infrastructure gone
Recovery: provision new infra from scratch using backups + IaC
RTO: hours to days
RPO: since last backup (hours)
Cost: very low (just storage)
```
 
Best for: non-critical workloads, development environments.
 
#### 2. Pilot Light
 
Keep a minimal version of the environment always running in DR region (just the database, replicated live). In a disaster, scale up application servers around it.
 
```
Normal: full production in ap-south-1
        minimal (just RDS replica) in us-east-1
Disaster: scale up EC2, ELB in us-east-1 around existing RDS
RTO: 10-30 minutes
RPO: seconds (continuous replication)
Cost: low (just replica DB)
```
 
Best for: critical databases with moderate recovery time tolerance.
 
#### 3. Warm Standby
 
Scaled-down but functional copy of production running in DR region. Scale up in disaster.
 
```
Normal: production (10 EC2 instances) in ap-south-1
        scaled-down standby (2 EC2, 1 RDS reader) in us-east-1
Disaster: scale up us-east-1 to full size, redirect DNS
RTO: minutes
RPO: seconds
Cost: medium (running 20-30% of production capacity continuously)
```
 
Best for: business-critical systems with tight RTO requirements.
 
#### 4. Multi-Site Active-Active (Most Expensive, Fastest)
 
Full production running simultaneously in multiple regions. Traffic distributed between both. Failover is instant.
 
```
Normal: 100% capacity in ap-south-1 AND us-east-1
        Route 53 Latency policy splits traffic between both
Disaster: Route 53 health check removes failed region
          100% traffic to healthy region
RTO: seconds (just DNS propagation)
RPO: near-zero (active-active sync)
Cost: very high (2x production cost)
```
 
Best for: mission-critical systems (banking, healthcare, e-commerce).
 
### RTO and RPO Summary
 
```
Faster Recovery ←──────────────────────────────────→ Slower Recovery
Lower Cost ←──────────────────────────────────────→ Higher Cost
 
Multi-Site     Warm Standby    Pilot Light    Backup & Restore
Active-Active
  RTO: secs     RTO: mins       RTO: 10-30min   RTO: hours-days
  RPO: ~0       RPO: secs       RPO: secs       RPO: hours
```
 
### AWS Backup
 
Centralised, fully managed backup service across AWS services.
 
#### Supported Services
 
EC2, EBS, RDS, Aurora, DynamoDB, DocumentDB, Neptune, EFS, FSx, Storage Gateway, S3.
 
#### Key Concepts
 
- **Backup Plan** — policy defining when to backup and how long to retain
- **Backup Vault** — encrypted logical container for backup recovery points
- **Recovery Points** — individual backups (snapshots)
- **Backup Vault Lock** — WORM (Write Once Read Many) — prevents deletion of backups. Used for compliance (ransomware protection).
 
#### Backup Plan Example
 
```
Rule: DailyBackup
  Schedule: cron(0 0 * * ? *)   → midnight every day
  Lifecycle: move to cold storage after 30 days
  Lifecycle: delete after 365 days
  Vault: production-backup-vault (encrypted with KMS)
  Copy to: another region (cross-region backup for DR)
```
 
#### AWS Backup for Cross-Account DR
 
```
Production Account (ap-south-1)
→ AWS Backup takes snapshots
→ Copies to DR Account (us-east-1)
→ DR account cannot be accessed by production account (blast radius isolation)
```
 
### Amazon S3 for Disaster Recovery
 
S3 is the foundation of most DR strategies because of its durability (11 nines) and features:
 
- **S3 Cross-Region Replication (CRR)** — automatic real-time replication to DR region
- **S3 Versioning** — recover from accidental deletion or overwrite
- **S3 Object Lock** — protect backups from ransomware deletion
- **S3 Lifecycle** — automatically archive older backups to Glacier to reduce cost
 
### Database DR
 
#### RDS
 
- **Automated backups** — point-in-time recovery within retention period
- **Manual snapshots** — survive instance deletion
- **Cross-region snapshots** — copy snapshot to DR region
- **Read replicas** — can be promoted to primary in minutes (RPO: seconds)
- **Multi-AZ** — synchronous standby, automatic failover (HA, not DR)
 
#### Aurora
 
- **Aurora Global Database** — cross-region read replica with < 1 second lag
- **Managed failover** — promote secondary region in < 1 minute
- **Backtrack** — rewind database to any point in the last 72 hours without restoring from snapshot
 
#### DynamoDB
 
- **Point-in-time recovery (PITR)** — restore to any second in last 35 days
- **Global Tables** — multi-region active-active (RPO: near-zero, automatic failover)
- **On-demand backups** — manual snapshots for long-term retention
 
### EC2 DR with AMIs
 
```
Production EC2 → Regular AMI snapshots → Copy AMI to DR region
Disaster: launch EC2 in DR region from AMI
          attach previously replicated data volumes
          update DNS to point to new instances
```
 
Automate with **AWS Backup** or **EC2 Image Builder** scheduled pipelines.
 
### Infrastructure as Code for DR
 
Terraform and CloudFormation make DR viable. If your production environment is defined as code:
 
```
Disaster in ap-south-1:
  1. Run Terraform apply in us-east-1
  2. Terraform recreates entire infrastructure
  3. Restore data from backups
  4. Update DNS
 
Without IaC: weeks of manual rebuild
With IaC: hours
```
 
This is why IaC is not just a DevOps convenience — it is a fundamental DR tool.
 
### DR Testing
 
A DR plan that is never tested is not a DR plan. Regular testing types:
 
| Test type | What you do | Disruption |
|---|---|---|
| Table-top exercise | Team walks through the plan verbally | None |
| Backup restoration test | Restore a backup to verify data integrity | None (test env) |
| Pilot light activation | Actually start up pilot light resources | None (test env) |
| Failover test | Switch production traffic to DR region | Possible brief impact |
| Full DR simulation | Take down primary region, run on DR only | Planned maintenance window |
 
**AWS Resilience Hub** — assess, validate, and track the resilience of your applications. Define RTO/RPO targets, get recommendations, run assessments.
 
---
 
## Quick Reference — Advanced AWS
 
### Choosing the Right Database
 
| Need | Service |
|---|---|
| Relational, managed, multi-engine | RDS |
| Relational, highest performance, auto-scaling storage | Aurora |
| NoSQL, serverless, millisecond latency | DynamoDB |
| In-memory caching | ElastiCache (Redis) |
| Petabyte analytics, BI | Redshift |
| Full-text search, log analytics | OpenSearch |
| Time series data | Timestream |
| Graph relationships | Neptune |
| Ledger / immutable transaction log | QLDB |
 
### Choosing the Right Compute
 
| Need | Service |
|---|---|
| Full OS control, persistent server | EC2 |
| Event-driven, short duration, no server management | Lambda |
| Docker containers, AWS-native | ECS (Fargate) |
| Kubernetes, portable | EKS |
| Deploy code, no infra management | Elastic Beanstalk |
| Batch jobs, large scale | AWS Batch |
| On-premises AWS infrastructure | Outposts |
 
### Choosing the Right Storage
 
| Need | Service |
|---|---|
| Persistent disk for EC2 | EBS |
| Shared file system across EC2 | EFS |
| Object storage, unlimited scale | S3 |
| Long-term archive, very cheap | S3 Glacier |
| Windows file server in cloud | FSx for Windows |
| HPC high-performance file system | FSx for Lustre |
| Connect on-premises to cloud storage | Storage Gateway |
 
### DR Strategy Selection
 
| RPO | RTO | Strategy | Cost |
|---|---|---|---|
| Hours | Hours-days | Backup and Restore | $ |
| Minutes-hours | 10-30 min | Pilot Light | $$ |
| Seconds-minutes | Minutes | Warm Standby | $$$ |
| Near-zero | Seconds | Multi-Site Active-Active | $$$$ |        
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
