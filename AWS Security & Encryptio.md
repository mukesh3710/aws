# AWS Security & Encryption
AWS provides a comprehensive suite of tools and services to ensure robust security and encryption of data, both in transit and at rest, across its ecosystem.

---

## Why Encryption?
### Encryption in Flight (TLS/SSL)
- Protects data as it travels between clients and servers.
- Uses protocols like TLS (Transport Layer Security) or SSL (Secure Sockets Layer).
- Example: HTTPS-secured websites.

### Server-Side Encryption at Rest
- AWS encrypts data after it is written to storage and decrypts it when accessed.
- Examples:
  - S3 server-side encryption.
  - RDS encrypted databases.

### Client-Side Encryption
- Data is encrypted before it is sent to AWS.
- Clients retain control of the encryption keys.

---

## AWS KMS (Key Management Service)
### KMS Key Types
- **Symmetric Keys:**
  - Used for encryption and decryption.
  - Never leave AWS KMS unencrypted.
- **Asymmetric Keys:**
  - Public/private key pairs.
  - Used for digital signatures and public-key encryption.

### KMS Key Policies
- Define access control for keys.
- Combine IAM policies and key policies for fine-grained permissions.

### KMS Multi-Region Keys
- Keys that are replicated across multiple regions.
- Simplifies key management for globally distributed applications.

---

## Data Encryption Use Cases
### Copying Snapshots Across Regions
- Ensure compliance and disaster recovery.
- KMS ensures snapshots remain encrypted.

### Copying Snapshots Across Accounts
- Share snapshots securely using KMS key policies.

### DynamoDB Global Tables and KMS Multi-Region Keys
- Ensures encryption for globally distributed DynamoDB tables.

### Global Aurora and KMS Multi-Region Keys
- Provides secure data encryption for Aurora clusters spanning multiple regions.

### S3 Replication Encryption Considerations
- Use KMS for replicating encrypted objects across S3 buckets in different regions.

---

## AMI Sharing Process
### Encrypted via KMS
- Share encrypted AMIs by granting access to KMS keys.

---

## AWS Systems Manager (SSM) Parameter Store
- Securely stores configuration data and secrets.

### SSM Parameter Store Hierarchy
- Organize parameters in a hierarchical structure (e.g., `/prod/db/password`).

### Standard and Advanced Parameter Tiers
- **Standard:** Basic storage with limited API throughput.
- **Advanced:** Larger parameter size and higher throughput.

### Parameter Policies (for Advanced Parameters)
- Automate parameter management (e.g., rotation, expiration).

---

## AWS Secrets Manager
- Securely stores and rotates secrets like database credentials and API keys.

### AWS Secrets Manager – Multi-Region Secrets
- Replicates secrets across multiple regions for disaster recovery.

---

## AWS Certificate Manager (ACM)
- Manages SSL/TLS certificates for AWS resources.

### ACM – Requesting Public Certificates
- Free public certificates for securing domains.

### ACM – Importing Public Certificates
- Use third-party certificates with AWS services.

### ACM – Integration with ALB
- Automatically integrates with Application Load Balancers to secure traffic.

### ACM – Integration with API Gateway
- Simplifies securing API Gateway endpoints with SSL certificates.

---

## AWS WAF – Web Application Firewall
- Protects applications from web-based attacks.

### WAF – Fixed IP While Using WAF with a Load Balancer
- Use AWS Global Accelerator to maintain fixed IPs for load balancers.

---

## AWS Shield: Protect from DDoS Attacks
- **AWS Shield Standard:** Basic protection for all AWS customers.
- **AWS Shield Advanced:** Enhanced protection, cost protection, and 24/7 support.

### AWS Firewall Manager
- Centralized management for WAF rules, Shield, and security groups.

### WAF vs. Firewall Manager vs. Shield
- **WAF:** Protects web applications.
- **Firewall Manager:** Centralizes WAF rule management.
- **Shield:** Protects against DDoS attacks.

---

## AWS Best Practices for DDoS Resiliency
### Edge Location Mitigation (BP1, BP3)
- Use services like CloudFront and Route 53 for edge-based DDoS mitigation.

### Best Practices for DDoS Mitigation
- Implement autoscaling.
- Use AWS WAF and Shield.

### Application Layer Defense
- Protect application-level resources using WAF rules and rate limiting.

### Attack Surface Reduction
- Minimize publicly exposed endpoints.

---

## Amazon GuardDuty
- Threat detection service that identifies anomalies and potential security risks.

---

## Amazon Inspector
- Automatically assesses applications for vulnerabilities and compliance.

### What Does Amazon Inspector Evaluate?
- Common vulnerabilities and exposures (CVEs).
- Compliance with security standards.

---

## AWS Macie
- Data security service that identifies sensitive data like PII in S3.
- Helps with compliance requirements like GDPR or HIPAA.
