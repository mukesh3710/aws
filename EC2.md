# Amazon EC2

Amazon Elastic Compute Cloud (EC2) provides scalable compute capacity in the cloud, allowing users to run virtual servers tailored to their specific needs.

## EC2 Sizing & Configuration Options

- Choose from a variety of instance types based on CPU, memory, storage, and networking requirements.
- Configure instances with specific AMIs (Amazon Machine Images) and attach storage volumes as needed.

## EC2 User Data

- User Data scripts run at instance launch to automate tasks, such as software installation or configuration.
- Scripts can be written in bash, PowerShell, or other supported scripting languages.

## EC2 Instance Types

### General Purpose
Balanced resources suitable for a variety of workloads.

### Compute Optimized
High-performance processors ideal for compute-intensive tasks like data analysis and machine learning.

### Memory Optimized
Designed for memory-intensive workloads such as databases and in-memory caching.

### Storage Optimized
High-speed storage capabilities for workloads requiring intensive read/write operations.

### EC2 Instance Types: Example
- **General Purpose**: t3.micro, t3.medium
- **Compute Optimized**: c5.large, c5.xlarge
- **Memory Optimized**: r5.large, r5.xlarge
- **Storage Optimized**: i3.large, i3.xlarge

## Security Groups

- Virtual firewalls controlling inbound and outbound traffic for instances.
- Configurable rules to allow or deny specific IP addresses, ports, or protocols.

### Security Groups: Deeper Dive
- Rules are **stateful**, meaning return traffic is automatically allowed.
- Inbound rules control incoming traffic, while outbound rules control outgoing traffic.

### Security Groups Diagram
```
Internet ---> Security Group ---> EC2 Instance
```

### Security Groups: Good to Know
- Each instance can be associated with multiple security groups.
- Security groups are region-specific.

### Referencing Other Security Groups Diagram
```
Security Group A (App) ---> Security Group B (DB)
```

## Classic Ports to Know
- HTTP: 80
- HTTPS: 443
- SSH: 22
- RDP: 3389

## EC2 Instance Connect

A browser-based SSH tool to access Linux instances securely without needing a local SSH client.

## EC2 Instances Purchasing Options

### EC2 On Demand
- Pay for compute capacity by the second or hour.
- Ideal for unpredictable workloads.

### EC2 Reserved Instances
- Commit to a specific instance type and region for 1 or 3 years.
- Offers significant cost savings compared to On-Demand pricing.

### EC2 Savings Plans
- Flexible pricing model offering lower rates for consistent usage across EC2, Fargate, and Lambda.

### EC2 Spot Instances
- Bid for unused EC2 capacity at reduced prices.
- Suitable for fault-tolerant, flexible applications.

### EC2 Dedicated Hosts
- Physical servers dedicated to your use, allowing license optimization.

### EC2 Dedicated Instances
- Instances running on dedicated hardware without sharing with other customers.

### EC2 Capacity Reservations
- Reserve capacity in a specific availability zone for any duration.

## Which Purchasing Option is Right for Me?
- **On-Demand**: Short-term, unpredictable workloads.
- **Reserved Instances**: Long-term, steady workloads.
- **Savings Plans**: Consistent usage across services.
- **Spot Instances**: Cost-sensitive, flexible, fault-tolerant tasks.
- **Dedicated Hosts/Instances**: Compliance or licensing needs.

## Price Comparison Example – m4.large – us-east-1
- **On-Demand**: $0.10/hour
- **Reserved Instance (1-year, standard)**: $0.075/hour
- **Spot**: $0.03/hour (price may vary)

## EC2 Spot Instance Requests, Pricing & How to Terminate Spot Instances

- **Spot Requests**: Specify desired capacity, instance type, and bid price.
- **Pricing**: Varies based on demand and supply of unused capacity.
- **Termination**: Instances can be terminated via the console, CLI, or API.

## Spot Fleets

- Manage multiple Spot Instance requests as a single entity.
- Optimize costs and maintain desired capacity across diverse instance types and availability zones.

---

# AWS Networking and Storage Concepts

## Private vs Public IP (IPv4)

- **Private IP**: Assigned to instances for internal communication within a VPC. Not accessible from the internet.
- **Public IP**: Assigned to instances for external communication. Accessible from the internet.

### Private vs Public IP (IPv4) Fundamental Differences

| Feature                | Private IP                     | Public IP                      |
|------------------------|--------------------------------|--------------------------------|
| Accessibility          | Internal network only         | Global internet access        |
| Cost                   | Free                          | Free (temporarily assigned)   |
| Persistence            | Retained on instance restart  | May change on restart         |

## Elastic IPs

- Static, public IPv4 addresses that can be reassigned to different instances within a region.
- Useful for maintaining a consistent public IP address.

## Placement Groups

Placement Groups allow instances to be placed in specific configurations to optimize performance or fault tolerance.

### Placement Groups: Cluster
- Instances are placed within a single availability zone.
- Low-latency, high-throughput workloads.

### Placement Groups: Spread
- Instances are spread across multiple hardware racks.
- High availability and fault tolerance.

### Placement Groups: Partition
- Instances are divided into logical partitions.
- Fault domains are isolated to reduce impact.

## Elastic Network Interfaces (ENI)

- Virtual network interfaces attached to EC2 instances.
- Can be used to assign multiple IP addresses to an instance.

## EC2 Hibernate

- Pauses an instance and saves its RAM to the root volume.
- On restart, the instance resumes from where it left off.

### EC2 Hibernate: Good to Know
- Supported on specific instance types.
- Requires EBS volumes encrypted with AWS-managed or customer-managed keys.

## EC2 – Instance Storage

- Temporary block-level storage attached to an instance.
- Data persists only during the instance lifecycle.

## EBS Volume

Elastic Block Store (EBS) provides durable, block-level storage for use with EC2 instances.

### EBS – Delete on Termination Attribute

- Determines whether an EBS volume is deleted when the associated instance is terminated.
- Configurable during instance launch or afterwards.

### EBS Snapshots

- Point-in-time backups of EBS volumes stored in Amazon S3.
- Used for disaster recovery and cloning volumes.

## AMI Overview

- Amazon Machine Images (AMI) provide templates for launching EC2 instances.
- Includes OS, software, and configuration settings.

### AMI Process (from an EC2 instance)

1. Create an instance.
2. Customize it with desired software and configurations.
3. Create an AMI from the instance.

## EC2 Instance Store

- Provides temporary storage for instances.
- Faster than EBS but non-persistent.

## EBS Volume Types

### EBS Volume Types Use Cases

- **General Purpose SSD (gp3/gp2)**: Balanced performance and cost.
- **Provisioned IOPS (PIOPS) SSD (io1/io2)**: High-performance applications.
- **Hard Disk Drives (HDD)**: Cost-effective for infrequent or sequential access.

### EBS Multi-Attach – io1/io2 Family

- Allows multiple EC2 instances to attach to a single io1/io2 volume.
- Use cases: Shared storage for clustered applications.

### EBS Encryption

- Encrypts data at rest, in transit, and in snapshots.

#### Encryption: Encrypt an Unencrypted EBS Volume
1. Create a snapshot of the volume.
2. Copy the snapshot with encryption enabled.
3. Create a new volume from the encrypted snapshot.
4. Attach the new volume to the instance.

## Amazon EFS – Elastic File System

- Scalable file storage for use with EC2.
- Automatically grows and shrinks as data is added or removed.

### EFS – Performance & Storage Classes

- **Performance Modes**: General Purpose and Max I/O.
- **Storage Classes**: Standard and Infrequent Access.

## EBS vs EFS – Elastic Block Storage

- **EBS**: Block storage attached to a single instance.
- **EFS**: Network file system accessible by multiple instances.

## EBS vs EFS – Elastic File System

| Feature             | EBS                            | EFS                            |
|---------------------|--------------------------------|--------------------------------|
| Accessibility       | Single instance               | Multiple instances            |
| Storage Type        | Block storage                 | File system                   |
| Use Cases           | Databases, boot volumes       | Shared storage, web serving   |

---
