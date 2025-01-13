# Amazon Route 53 and DNS

## What is DNS?
- **Definition**: Domain Name System (DNS) translates domain names (e.g., example.com) into IP addresses.
- **Purpose**: Makes it easier for users to access websites without remembering IP addresses.

## DNS Terminologies
- **Domain**: A unique name identifying a website (e.g., amazon.com).
- **IP Address**: Numerical address of a server (e.g., 192.168.1.1).
- **Zone File**: A file containing DNS records for a domain.
- **Nameserver**: Server that responds to DNS queries.

## How DNS Works
1. User enters a domain name in a browser.
2. Browser sends a query to a DNS resolver.
3. Resolver contacts the authoritative nameserver.
4. Nameserver returns the corresponding IP address.
5. Browser uses the IP address to connect to the website.

## Amazon Route 53
- Fully managed DNS web service by AWS.
- Provides domain registration, DNS routing, and health checking.

### Route 53 – Records
- DNS records provide mappings between domain names and their corresponding IP addresses or endpoints.

### Route 53 – Record Types
- **A**: Maps a domain to an IPv4 address.
- **AAAA**: Maps a domain to an IPv6 address.
- **CNAME**: Maps a domain to another domain name.
- **MX**: Directs email to mail servers.
- **TXT**: Stores text information for domains.

### Route 53 – Hosted Zones
- **Definition**: A container for DNS records for a domain.
- Types:
  - **Public Hosted Zone**: For domains accessible on the internet.
  - **Private Hosted Zone**: For domains accessible only within a VPC.

### Route 53 – Records TTL (Time To Live)
- Determines how long a DNS resolver caches a record before querying Route 53 again.
- Default TTL is 300 seconds.

### CNAME vs Alias
- **CNAME**: Maps one domain to another; does not support root domain (e.g., example.com).
- **Alias**: Maps a domain to an AWS resource (e.g., CloudFront, S3); supports root domain.

### Route 53 – Alias Records
- Alias records provide a route to AWS resources.

#### Route 53 – Alias Records Targets
- Common targets include:
  - Elastic Load Balancers (ELB).
  - Amazon S3 buckets.
  - CloudFront distributions.

## Route 53 – Routing Policies
- Determine how Route 53 responds to DNS queries.

### Routing Policies – Simple
- Default policy that routes traffic to a single resource.

### Routing Policies – Weighted
- Distributes traffic across multiple resources based on assigned weights.

### Routing Policies – Latency-Based
- Routes traffic to the resource with the lowest network latency.

## Route 53 – Health Checks
- Monitor the health of endpoints and route traffic accordingly.

### Health Checks – Monitor an Endpoint
- Regularly checks the availability of an endpoint.
- Automatically removes unhealthy endpoints.

### Route 53 – Calculated Health Checks
- Combines results of multiple health checks to determine overall health.

### Health Checks – Private Hosted Zones
- Use Route 53 Resolver to monitor endpoints within a VPC.

### Routing Policies – Failover (Active-Passive)
- Routes traffic to a primary resource unless it becomes unhealthy, then switches to a secondary resource.

### Routing Policies – Geolocation
- Routes traffic based on the user's geographic location.

### Routing Policies – Geoproximity
- Routes traffic based on geographic proximity and bias settings.

### Routing Policies – IP-Based Routing
- Directs traffic based on the user's IP address.

### Routing Policies – Multi-Value
- Returns multiple IP addresses for DNS queries to improve availability.

## Domain Registrar vs. DNS Service
- **Domain Registrar**: Manages domain registration (e.g., GoDaddy, Namecheap).
- **DNS Service**: Handles domain name resolution (e.g., Route 53).

### GoDaddy as Registrar & Route 53 as DNS Service
- Register a domain with GoDaddy.
- Update nameservers to point to Route 53.
- Manage DNS records using Route 53.

### 3rd Party Registrar with Amazon Route 53
- Domains registered with third-party providers can still use Route 53 for DNS by updating the domain's nameservers.

---
