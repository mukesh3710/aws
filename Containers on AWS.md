# Containers on AWS

## What is Docker?
Docker is an open-source platform designed to automate the deployment of applications inside lightweight, portable containers. Containers bundle an application and its dependencies, ensuring it runs consistently across different computing environments.

---

## Docker on an OS
Docker runs on top of an operating system (OS), utilizing the OS kernel to create isolated environments for containers. These containers share the OS kernel but operate as if they have their own dedicated resources.

---

## Where are Docker images stored?
Docker images are stored in repositories, such as Docker Hub, Amazon Elastic Container Registry (ECR), or private registries. These images serve as templates for creating containers.

---

## Docker vs. Virtual Machines
| Feature             | Docker Containers                | Virtual Machines                 |
|---------------------|----------------------------------|-----------------------------------|
| Resource Usage      | Lightweight and efficient        | Heavy and resource-intensive     |
| Isolation           | Shares OS kernel                | Full OS isolation                |
| Startup Time        | Fast (seconds)                  | Slower (minutes)                 |
| Portability         | Highly portable                 | Less portable                    |

---

## Getting Started with Docker
1. **Install Docker**: Download and install Docker on your machine.
2. **Pull Images**: Use `docker pull <image>` to download images.
3. **Run Containers**: Create a container with `docker run`.
4. **Manage Containers**: Use commands like `docker ps`, `docker stop`, and `docker rm` to manage containers.

---

## Docker Containers Management on AWS
AWS provides several services to manage Docker containers efficiently:
- Amazon ECS (Elastic Container Service)
- Amazon EKS (Elastic Kubernetes Service)
- AWS App Runner

---

## Amazon ECS - EC2 Launch Type
In this mode, ECS runs containers on a fleet of EC2 instances managed by the user. Key features:
- Complete control over EC2 instances.
- Requires scaling and maintenance of the underlying infrastructure.

---

## Amazon ECS – Fargate Launch Type
Fargate is a serverless compute engine for ECS, eliminating the need to manage EC2 instances. Key features:
- Pay for vCPU and memory usage.
- Simplifies scaling and deployment.

---

## Amazon ECS – IAM Roles for ECS
IAM roles for ECS allow tasks and services to access AWS resources securely. Examples:
- Allowing access to S3 buckets.
- Enabling access to secrets in AWS Secrets Manager.

---

## Amazon ECS – Load Balancer Integrations
ECS can integrate with:
- **Application Load Balancer (ALB)**: For HTTP/HTTPS traffic.
- **Network Load Balancer (NLB)**: For TCP/UDP traffic.

---

## Amazon ECS – Data Volumes (EFS)
ECS supports data persistence by integrating with Amazon Elastic File System (EFS). This allows tasks to share data across multiple containers.

---

## ECS Service Auto Scaling
ECS can automatically scale services based on:
- CPU or memory utilization.
- Custom metrics using CloudWatch.

---

## EC2 Launch Type – Auto Scaling EC2 Instances
With EC2 launch type, you can configure Auto Scaling groups to dynamically scale ECS instances based on cluster requirements.

---

## ECS Scaling – Service CPU Usage Example
Scaling policy example:
- Target CPU utilization: 50%.
- Minimum tasks: 1.
- Maximum tasks: 10.

---

## ECS tasks invoked by EventBridge
Amazon EventBridge can trigger ECS tasks based on:
- Event patterns (e.g., S3 object creation).
- Schedule-based rules.

---

## ECS tasks invoked by EventBridge Schedule
Schedule ECS tasks using EventBridge to:
- Run periodic jobs.
- Trigger backups or maintenance tasks.

---

## ECS – SQS Queue Example
ECS can process messages from an Amazon SQS queue. Workflow:
1. Messages are pushed to the SQS queue.
2. ECS tasks consume and process the messages.

---

## ECS – Intercept Stopped Tasks using EventBridge
EventBridge can monitor ECS task lifecycle events, allowing users to:
- Log stopped tasks.
- Trigger workflows based on task termination.

---

## Amazon ECR
Amazon Elastic Container Registry (ECR) is a fully managed Docker container registry. Features:
- Highly available and secure.
- Integrated with ECS, EKS, and AWS Lambda.

---

## Amazon EKS Overview
Amazon Elastic Kubernetes Service (EKS) is a managed service to run Kubernetes on AWS without managing the control plane.

### Amazon EKS - Diagram
Visual representation of the EKS architecture:
- Managed Kubernetes control plane.
- Worker nodes running on EC2 or Fargate.

---

## Amazon EKS – Node Types
1. **Managed Node Groups**: AWS manages the lifecycle of EC2 instances.
2. **Self-Managed Nodes**: User-managed EC2 instances.
3. **Fargate Nodes**: Serverless Kubernetes nodes.

---

## Amazon EKS – Data Volumes
EKS integrates with EBS, EFS, and FSx for persistent storage:
- **EBS**: Block storage.
- **EFS**: File storage shared across pods.
- **FSx**: High-performance file systems.

---

## AWS App Runner
AWS App Runner is a fully managed service to deploy and scale web applications and APIs directly from source code or container images. Features:
- Simplified deployment pipeline.
- Auto-scaling based on traffic.

