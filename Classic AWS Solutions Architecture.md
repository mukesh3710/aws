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
