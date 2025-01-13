# Amazon VPC and Networking in AWS
Amazon Virtual Private Cloud (VPC) enables you to launch AWS resources into a virtual network. Below are detailed explanations of various VPC components and networking topics in AWS.

---

## Amazon VPC
- Provides a virtual network isolated from other AWS customers.
- Offers full control over IP addressing, subnets, route tables, and gateways.

---

## VPC Components
- **CIDR (IPv4/IPv6):** Defines the IP address range for your VPC.
- **Subnets:** Divide the VPC's IP range into smaller segments.
- **Route Tables:** Determine how traffic is routed.
- **Internet Gateway (IGW):** Enables internet access.
- **NAT Gateway/Instance:** Facilitates outbound internet traffic for private subnets.
- **Security Groups:** Act as virtual firewalls at the instance level.
- **Network Access Control Lists (NACLs):** Provide subnet-level security.

---

## Understanding CIDR – IPv4
- CIDR (Classless Inter-Domain Routing) specifies IP ranges, e.g., `192.168.0.0/16`.
- The `/16` indicates the subnet mask, which defines the number of available IPs.

## Understanding CIDR – Subnet Mask
- A `/24` subnet mask allows 256 IPs, while a `/16` mask allows 65,536 IPs.
- Plan subnets based on workload requirements.

## Public vs. Private IP (IPv4)
- **Public IP:** Reachable over the internet.
- **Private IP:** Restricted to internal communication within the VPC.

---

## Default VPC
- Automatically created in every AWS region.
- Includes a public subnet and an internet gateway.

## VPC in AWS – IPv4
- Assign an IPv4 CIDR block when creating a VPC.
- Cannot modify the CIDR block after creation.

---

## VPC – Subnet (IPv4)
- Divide a VPC's IP range into smaller subnets.
- Subnets can be public or private based on routing.

## Internet Gateway (IGW)
- Enables internet access for public subnets.
- Attach an IGW to the VPC and update route tables.

## State of Hands-on - Adding Subnets, Adding Internet Gateway, Editing Route Tables
- **Add Subnets:** Allocate IP ranges.
- **Add IGW:** Attach to the VPC.
- **Edit Route Tables:** Configure routes for internet access.

---

## Bastion Hosts
- Acts as a secure entry point to access private instances.

## NAT Instance
- Enables outbound internet traffic for private subnets.
- Requires manual scaling and configuration.

## NAT Gateway
- Managed service for high availability and scalability.

### NAT Gateway with High Availability
- Deploy NAT Gateways in multiple Availability Zones (AZs).

### NAT Gateway vs. NAT Instance
- **NAT Gateway:** Managed, scalable, higher cost.
- **NAT Instance:** Customizable, lower cost, manual scaling.

---

## Security Groups & NACLs
### Network Access Control List (NACL)
- Subnet-level security.
- Stateless; requires explicit inbound and outbound rules.

### Default NACL
- Allows all inbound and outbound traffic by default.

### Ephemeral Ports
- Temporary ports used for short-term communication.

### NACL with Ephemeral Ports
- Configure rules to allow ephemeral ports for specific services.

### Create NACL Rules for Each Target Subnet CIDR
- Apply tailored rules for subnets.

### Security Group vs. NACLs
- **Security Groups:** Instance-level, stateful.
- **NACLs:** Subnet-level, stateless.

---

## VPC Peering
- Connects two VPCs for resource sharing.

## VPC Endpoints
- Private connections to AWS services without using the internet.

### VPC Endpoints (AWS PrivateLink)
- Securely connect services across VPCs.

### Types of Endpoints
- **Interface Endpoint:** Connects to AWS services.
- **Gateway Endpoint:** Supports S3 and DynamoDB.

### Gateway or Interface Endpoint for S3?
- Use Gateway Endpoint for S3 for cost efficiency.

---

## Lambda in VPC Accessing DynamoDB
- Requires VPC endpoints to connect securely without internet access.

---

## VPC Flow Logs
- Capture network traffic logs for analysis.

### VPC Flow Logs – Troubleshoot SG & NACL Issues
- Diagnose blocked traffic.

### VPC Flow Logs – Architectures
- Integrate with CloudWatch or S3 for storage and analysis.

---

## AWS Site-to-Site VPN
- Securely connects on-premises networks to AWS.

### Site-to-Site VPN Connections
- Establishes IPSec connections.

### AWS VPN CloudHub
- Connects multiple remote networks to a VPC.

---

## Direct Connect (DX)
### Direct Connect Gateway
- Connects multiple VPCs or on-premises networks.

### Direct Connect – Connection Types
- Dedicated or hosted connections.

### Direct Connect – Encryption
- Encrypts data using MACsec or VPN.

### Direct Connect – Resiliency
- Provides redundant connections.

### Site-to-Site VPN Connection as a Backup
- Ensures high availability.

---

## Network Topologies Can Become Complicated
### Transit Gateway
- Centralizes VPC and on-premises network connectivity.

### Transit Gateway: Site-to-Site VPN ECMP
- Equal Cost Multipath for redundancy.

### Transit Gateway: Throughput with ECMP
- Increases bandwidth using parallel connections.

### Transit Gateway – Share Direct Connect Between Multiple Accounts
- Simplifies cross-account access.

---

## VPC – Traffic Mirroring
- Duplicates traffic for monitoring or troubleshooting.

---

## What is IPv6?
- 128-bit IP addressing scheme for vast address space.

### IPv6 in VPC
- Dual-stack mode supports IPv4 and IPv6.

### IPv6 Troubleshooting
- Ensure correct routing and security configurations.

### Egress-Only Internet Gateway
- Supports IPv6 outbound internet traffic.

### IPv6 Routing
- Configure routes specific to IPv6 traffic.

---

## Networking Costs in AWS per GB - Simplified
- **Data Transfer In:** Free.
- **Data Transfer Out:** Charged per GB.

### Minimizing Egress Traffic Network Cost
- Use edge locations and caching (e.g., CloudFront).

### S3 Data Transfer Pricing – Analysis for USA
- Consider cross-region transfer costs.

### Pricing: NAT Gateway vs Gateway VPC Endpoint
- Gateway endpoints are more cost-effective for services like S3.

---

## Network Protection on AWS
### AWS Network Firewall
- Managed firewall for traffic filtering.

### Network Firewall – Fine-Grained Controls
- Granular control over network traffic using custom rules.
