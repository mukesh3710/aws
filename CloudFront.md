# CloudFront & Global Accelerator

## Amazon CloudFront
Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to users globally with low latency and high transfer speeds.

### CloudFront – Origin
- **Origin** is the source of the files that CloudFront will distribute. Examples include:
  - Amazon S3 buckets
  - HTTP/HTTPS servers such as ALB, EC2 instances, or on-premises servers.

### CloudFront at a High Level
- Users request content through CloudFront.
- The request is routed to the nearest edge location.
- If the content is cached, it is served directly.
- If not, CloudFront retrieves it from the origin and caches it for future requests.

### CloudFront – S3 as an Origin
- An Amazon S3 bucket can act as the origin for CloudFront to distribute static content globally.
- Use case: Static website hosting with fast, global delivery.

### CloudFront vs S3 Cross Region Replication
| **Feature**               | **CloudFront**                     | **S3 Cross Region Replication** |
|---------------------------|------------------------------------|----------------------------------|
| Purpose                  | Global content caching and delivery| Replicating S3 data across regions|
| Latency                  | Low latency using edge locations   | Depends on replication time     |
| Cost                     | Data transfer and request costs    | Storage and replication costs   |
| Use Case                 | Speed up content delivery          | Data backup and disaster recovery|

### CloudFront – ALB or EC2 as an Origin
- Application Load Balancer (ALB) or EC2 instances can serve dynamic content through CloudFront.
- Ideal for delivering APIs or dynamic websites.

### CloudFront Geo Restriction
- Restrict content access based on the geographic location of the viewer.
- Examples:
  - Allow only specific countries.
  - Block specific countries.

### CloudFront - Pricing
- **Data Transfer**: Outbound data transfer to viewers.
- **Requests**: Number of HTTP/HTTPS requests.
- **Additional Costs**: Cache invalidations and real-time logs.

### CloudFront – Price Classes
- Price classes allow cost optimization by limiting edge locations based on geography:
  - **Price Class 100**: Cheapest; limits to a few regions.
  - **Price Class 200**: Moderate cost; broader coverage.
  - **Price Class All**: Most expensive; uses all edge locations globally.

### CloudFront – Cache Invalidations
- Used to remove outdated content from edge locations.
- Example: Updating a static website’s image.
- Charges apply for invalidations beyond the free limit.

## Global Users for Our Application
Applications serving global users benefit from:
- **Low latency**: Using edge locations close to users.
- **High availability**: Leveraging redundant infrastructure.

### Unicast IP vs Anycast IP
- **Unicast IP**: Single, specific routing path.
- **Anycast IP**: Routes traffic to the nearest endpoint, improving latency and fault tolerance.

## AWS Global Accelerator
- A network service that improves the availability and performance of applications with global users.
- Provides static IP addresses for applications, redirecting traffic to the optimal AWS endpoint based on health and proximity.

### AWS Global Accelerator vs CloudFront
| **Feature**             | **Global Accelerator**               | **CloudFront**                     |
|-------------------------|--------------------------------------|------------------------------------|
| Purpose                | Optimize application performance    | Cache and deliver content globally|
| Use Case               | Latency-sensitive applications       | Static and dynamic content delivery|
| IP Address             | Static Anycast IP                   | DNS-based routing                  |
| Caching                | No caching                          | Content caching at edge locations  |
| Protocol Support       | TCP/UDP                             | HTTP/HTTPS                         |

---

