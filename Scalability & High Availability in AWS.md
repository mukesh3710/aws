# Scalability & High Availability in AWS

## Scalability & High Availability

### Vertical Scalability
- **Definition**: Increasing the capacity of a single resource (e.g., upgrading instance type for more CPU, memory).
- **Use Case**: Monolithic applications.
- **Limitation**: Hardware constraints.

### Horizontal Scalability
- **Definition**: Adding more resources (e.g., EC2 instances) to distribute the load.
- **Use Case**: Modern distributed systems.
- **Benefits**: Increased fault tolerance and capacity.

### High Availability
- **Definition**: Ensures a system is operational with minimal downtime.
- **Achieved Through**: Redundancy, load balancing, and failover strategies.

## High Availability & Scalability for EC2
- Use **Auto Scaling Groups** for scalability.
- Employ **Elastic Load Balancers** for high availability.
- Leverage multiple **Availability Zones**.

## What is Load Balancing?

- **Definition**: Distributes incoming traffic across multiple targets (e.g., EC2 instances).
- **Purpose**: Improve fault tolerance and ensure high availability.

### Why Use a Load Balancer?
- Redundancy and fault tolerance.
- Efficient utilization of resources.
- Scalability and performance optimization.

### Why Use an Elastic Load Balancer?
- Fully managed service.
- Scales automatically.
- Supports multiple protocols and routing strategies.

## Health Checks
- Regularly monitor target instances' health.
- Automatically route traffic only to healthy instances.

## Types of Load Balancer on AWS
1. Classic Load Balancers (v1)
2. Application Load Balancers (v2)
3. Network Load Balancers (v2)
4. Gateway Load Balancers

## Load Balancer Security Groups
- Control traffic flow to and from the load balancer.
- Define rules for allowed IPs, ports, and protocols.

## Classic Load Balancers (v1)
- Original load balancer type.
- Supports basic HTTP, HTTPS, and TCP traffic.
- Limited features compared to modern load balancers.

## Application Load Balancer (v2)
- Optimized for HTTP/HTTPS traffic.
- Supports advanced features like routing, WebSockets, and monitoring.

### Application Load Balancer (v2): HTTP-Based Traffic
- Ideal for web applications.
- Supports path-based and host-based routing.

### Application Load Balancer (v2): Target Groups
- Group of targets (e.g., EC2 instances) for traffic distribution.

### Application Load Balancer (v2): Query Strings/Parameters Routing
- Routes traffic based on query strings or parameters.

### Application Load Balancer (v2): Good to Know
- Integrates with AWS Certificate Manager for SSL.
- Supports cross-zone load balancing.

## Network Load Balancer (v2)
- Handles high throughput and low latency requirements.
- Operates at Layer 4 (TCP).

### Network Load Balancer (v2): TCP (Layer 4) Based Traffic
- Efficient for non-HTTP protocols.
- Ideal for real-time systems.

### Network Load Balancer: Target Groups
- Manages traffic routing for specific targets.

## Gateway Load Balancer
- Facilitates deployment of virtual appliances like firewalls and intrusion detection systems.

### Gateway Load Balancer: Target Groups
- Groups appliances for traffic flow management.

## Sticky Sessions (Session Affinity)
- Ensures user requests are consistently routed to the same target.

### Sticky Sessions: Cookie Names
- Uses cookies to maintain session affinity.

## Cross-Zone Load Balancing
- Distributes traffic evenly across all targets in different Availability Zones.

## SSL/TLS - Basics
- Ensures secure communication over the internet.
- TLS is the successor to SSL.

## Load Balancer - SSL Certificates
- Encrypts communication between clients and load balancers.

### SSL – Server Name Indication (SNI)
- Allows multiple SSL certificates on a single load balancer.

### Elastic Load Balancers – SSL Certificates
- Use AWS Certificate Manager to provision and manage certificates.

## Connection Draining
- Ensures active requests are completed before deregistering a target.

## What’s an Auto Scaling Group?
- Automatically manages a group of EC2 instances to meet desired capacity.

### Auto Scaling Group in AWS
- Launches or terminates instances based on scaling policies.

### Auto Scaling Group in AWS With Load Balancer
- Integrates with load balancers to maintain high availability.

### Auto Scaling Group Attributes
- **Minimum Size**: Minimum number of instances.
- **Maximum Size**: Maximum number of instances.
- **Desired Capacity**: Target number of instances.

## Auto Scaling - CloudWatch Alarms & Scaling
- Monitors metrics and triggers scaling actions.

### Auto Scaling Groups: Dynamic Scaling Policies
- Adjusts capacity based on demand patterns.

### Auto Scaling Groups: Predictive Scaling
- Uses machine learning to forecast and scale proactively.

### Good Metrics to Scale On
- CPU utilization, network traffic, request count, custom metrics.

### Auto Scaling Groups: Scaling Cooldowns
- Pause between scaling actions to stabilize the system.

---
