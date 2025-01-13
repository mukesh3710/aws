# Classic AWS Solutions Architecture for a Stateless Web App: "What Time Is It"

## 1. Starting Simple in EC2
- Launch a single EC2 instance to host the application.
- Choose an appropriate instance type (e.g., `t2.micro` for low-cost testing).
- Configure the security group to allow HTTP (port 80) and HTTPS (port 443) traffic.
- Deploy the application code to the EC2 instance.
- Verify functionality by accessing the app through the instance's public IP or DNS.

## 2. Scaling Vertically
- Identify performance bottlenecks in the application.
- Upgrade the EC2 instance to a larger instance type (e.g., from `t2.micro` to `m5.large`).
- Monitor performance using CloudWatch metrics.
- Consider vertical scaling only as a temporary solution since it has limits.

## 3. Scaling Horizontally
- Launch additional EC2 instances to handle increased traffic.
- Ensure all instances run the same version of the application.
- Use Elastic IPs or private IPs for inter-instance communication.
- Update the security group rules to allow communication between instances if necessary.

## 4. Scaling Horizontally, Adding and Removing Instances
- Implement a process to manually add or remove instances as traffic changes.
- Use an Elastic Load Balancer (ELB) to distribute traffic across instances.
- Update the DNS configuration to point to the ELB instead of individual instance IPs.
- Monitor traffic and instance health using ELB health checks.

## 5. Scaling Horizontally, with a Load Balancer
- Use an Application Load Balancer (ALB) to handle HTTP/HTTPS traffic.
- Configure target groups for the EC2 instances.
- Enable session stickiness if needed for stateful workloads.
- Use ALB health checks to automatically remove unhealthy instances.
- Ensure DNS is updated to route traffic to the ALB.

## 6. Scaling Horizontally, with an Auto-Scaling Group
- Create an Auto Scaling Group (ASG) to manage EC2 instances.
- Define scaling policies based on metrics like CPU utilization or network traffic.
- Set minimum and maximum instance limits in the ASG.
- Configure CloudWatch alarms to trigger scaling events.
- Test scaling by simulating increased or decreased load.

## 7. Making Our App Multi-AZ (Minimum 2 AZs)
- Modify the Auto Scaling Group to span at least two Availability Zones (AZs).
- Update the Elastic Load Balancer to distribute traffic across instances in multiple AZs.
- Use a Multi-AZ deployment to improve availability and fault tolerance.
- Reserve capacity in each AZ to ensure sufficient resources during failover.
- Test failover scenarios by terminating instances in one AZ and observing traffic distribution.

---

# Classic AWS Solutions Architecture for a Stateful Web App: "MyClothes.com"

## Overview
**MyClothes.com** is an e-commerce website allowing users to buy clothes online. To ensure scalability, reliability, and a seamless user experience, we need to maintain horizontal scalability while preserving user data such as shopping carts and personal details.

---

## 1. Starting Simple with EC2 and a Database
- **Application Deployment**:
  - Launch a single EC2 instance to host the application.
  - Use a framework or language suitable for e-commerce (e.g., Node.js, Java, or Python).
  - Deploy the app code and connect it to a database.
- **Database Setup**:
  - Use Amazon RDS for a managed relational database.
  - Store user data such as addresses and shopping cart details in RDS.
  - Enable automated backups and Multi-AZ for high availability.
- **Security**:
  - Configure security groups to allow HTTP (port 80) and HTTPS (port 443) traffic to the EC2 instance.
  - Allow the EC2 instance to communicate with RDS over the appropriate port (default: 3306 for MySQL).

---

## 2. Ensuring Statelessness
- **Session Management**:
  - Use Amazon ElastiCache (Redis or Memcached) to store session data.
  - Store shopping cart details in ElastiCache to ensure sessions are stateless.
- **Database for Persistent Data**:
  - Keep user addresses and order history in RDS for long-term storage.
- **Best Practices**:
  - Design the app to fetch cart details and sessions from ElastiCache, not from the EC2 instance.

---

## 3. Scaling Horizontally
- **Load Balancer Setup**:
  - Deploy an Application Load Balancer (ALB) to distribute traffic across multiple EC2 instances.
  - Configure ALB health checks to ensure only healthy instances receive traffic.
- **Auto Scaling Group (ASG)**:
  - Create an ASG to automatically add or remove EC2 instances based on traffic patterns.
  - Define scaling policies using CloudWatch metrics like CPU utilization or request count.
- **Data Consistency**:
  - Ensure ElastiCache and RDS are accessible to all EC2 instances to maintain consistency.

---

## 4. Multi-AZ Deployment
- **EC2 Deployment**:
  - Deploy EC2 instances across at least two Availability Zones (AZs) for fault tolerance.
  - Update the Auto Scaling Group to distribute instances evenly across AZs.
- **RDS Multi-AZ**:
  - Enable Multi-AZ on the RDS database to ensure high availability.
  - Use Read Replicas for read-heavy operations, reducing the load on the primary database.

---

## 5. Scaling and Managing User Data
- **Shopping Cart**:
  - Store shopping cart sessions in ElastiCache for fast, in-memory access.
  - Implement fallback mechanisms to persist carts to RDS if needed.
- **User Details**:
  - Keep all user details (e.g., addresses) in RDS.
  - Ensure proper indexing to maintain query performance.
- **High Availability**:
  - Enable replication and failover for ElastiCache.

---

## 6. Reserving Capacity
- **Capacity Planning**:
  - Use Reserved Instances for EC2 to save costs on predictable workloads.
  - Reserve RDS capacity for consistent performance and availability.
- **Traffic Spikes**:
  - Configure Auto Scaling policies for sudden traffic spikes (e.g., Black Friday sales).
  - Use AWS WAF to protect against web attacks.

---

## 7. Monitoring and Optimization
- **Monitoring Tools**:
  - Use AWS CloudWatch to monitor EC2, RDS, and ElastiCache performance metrics.
  - Set up alarms for resource utilization and latency.
- **Cost Optimization**:
  - Use Savings Plans for predictable usage patterns.
  - Analyze cost and usage reports to optimize resource allocation.

---

# Classic AWS Solutions Architecture for a Stateful Web App: "MyWordPress.com"

## Overview
**MyWordPress.com** aims to be a fully scalable WordPress website capable of handling traffic fluctuations, managing picture uploads, and securely storing user data and blog content in a MySQL database.

---

## 1. Setting Up the WordPress Application
- **EC2 for WordPress Hosting**:
  - Launch an EC2 instance with a web server (e.g., Apache or Nginx).
  - Install WordPress using prebuilt images or manual installation.
  - Configure the instance with security groups to allow HTTP (port 80) and HTTPS (port 443).

---

## 2. Database Setup for User Data and Blog Content
- **RDS MySQL**:
  - Launch an Amazon RDS MySQL instance to store WordPress data (user information, blog content, etc.).
  - Enable Multi-AZ for high availability and automated backups.
  - Optimize database performance with read replicas for read-heavy operations.
- **Connection Configuration**:
  - Update the `wp-config.php` file in WordPress to connect to the RDS MySQL instance.

---

## 3. Managing Picture Uploads
- **Amazon S3 for Media Storage**:
  - Create an S3 bucket to store WordPress media files (e.g., pictures, videos).
  - Install and configure a WordPress plugin (e.g., WP Offload Media) to offload media uploads to S3.
  - Use S3 bucket policies to secure access to media files.
- **Amazon CloudFront**:
  - Configure CloudFront as a content delivery network (CDN) for the S3 bucket.
  - Enable caching and optimize media delivery for a better user experience.

---

## 4. Scaling the WordPress Application
- **Load Balancer**:
  - Use an Application Load Balancer (ALB) to distribute traffic across multiple WordPress EC2 instances.
  - Configure health checks to ensure only healthy instances serve traffic.
- **Auto Scaling Group (ASG)**:
  - Create an ASG to automatically add or remove EC2 instances based on traffic patterns.
  - Define scaling policies using metrics like CPU utilization and request count.

---

## 5. Ensuring Statelessness
- **ElastiCache for Session Management**:
  - Use Amazon ElastiCache (Redis or Memcached) to store session data for a stateless WordPress architecture.
  - Ensure that session data is shared across all EC2 instances.
- **Shared File System**:
  - Use Amazon EFS (Elastic File System) for shared storage of WordPress files (e.g., themes, plugins).
  - Mount the EFS file system to all WordPress EC2 instances.

---

## 6. Multi-AZ and Disaster Recovery
- **Multi-AZ Setup**:
  - Deploy EC2 instances in at least two Availability Zones for high availability.
  - Ensure the RDS instance is configured for Multi-AZ deployment.
- **Backup and Restore**:
  - Enable automated backups for RDS.
  - Use S3 Versioning to manage media file versions.

---

## 7. Security Best Practices
- **IAM Roles**:
  - Assign IAM roles to EC2 instances to grant them access to S3, CloudFront, and ElastiCache.
- **Security Groups**:
  - Restrict access to EC2, RDS, and EFS with tightly configured security groups.
- **SSL/TLS**:
  - Use ACM (AWS Certificate Manager) to manage SSL certificates for HTTPS traffic.

---

## 8. Monitoring and Cost Optimization
- **Monitoring**:
  - Use Amazon CloudWatch to monitor EC2, RDS, and S3 performance.
  - Set up alarms for high CPU utilization, database latency, and S3 access errors.
- **Cost Optimization**:
  - Use Reserved Instances or Savings Plans for predictable workloads.
  - Analyze AWS Cost Explorer reports to optimize resource usage.

---

