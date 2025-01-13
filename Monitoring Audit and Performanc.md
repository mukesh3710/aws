# AWS Monitoring, Audit, and Performance Overview
AWS provides a robust set of services to monitor, audit, and optimize application performance and infrastructure.

---

## Amazon CloudWatch Metrics
- **Type:** Real-time monitoring service.
- **Key Features:**
  - Collects and visualizes metrics from AWS resources and applications.
  - Supports custom metrics and high-resolution metrics.
- **Use Cases:** Monitor resource usage, application health, and operational trends.

### CloudWatch Metric Streams
- Streams CloudWatch metrics to a destination like Amazon S3 or analytics services.
- Enables near real-time processing and visualization of metrics.

---

## CloudWatch Logs
- **Type:** Centralized logging service.
- **Key Features:**
  - Collect, monitor, and store logs from AWS resources and applications.
  - Search and analyze log data.

### CloudWatch Logs – Sources
- Log data sources include:
  - EC2 instances.
  - Lambda functions.
  - VPC Flow Logs.
  - RDS and CloudTrail logs.

### CloudWatch Logs Insights
- Provides a query language to analyze log data interactively.
- Use cases: Troubleshooting, trend analysis, and log pattern discovery.

### CloudWatch Logs – S3 Export
- Export logs to Amazon S3 for long-term retention or advanced analytics.

### CloudWatch Logs Subscriptions
- Stream log data to services like Amazon Elasticsearch, Kinesis, or Lambda.

### CloudWatch Logs Aggregation (Multi-Account & Multi-Region)
- Use AWS Organizations and centralized logging solutions to aggregate logs across accounts and regions.

### CloudWatch Logs for EC2
- Use the CloudWatch agent to push application and system logs from EC2 to CloudWatch Logs.

### CloudWatch Logs Agent & Unified Agent
- **Unified Agent:** Collects metrics and logs in a single agent.
- Supports application-level logs and additional system-level metrics.

### CloudWatch Unified Agent – Metrics
- Captures additional system metrics like memory, disk usage, and processes.

---

## CloudWatch Alarms
- **Type:** Alerting mechanism based on metric thresholds.
- **Key Features:**
  - Trigger actions like sending notifications or autoscaling.
  - Can monitor custom metrics.

### CloudWatch Alarm Targets
- Targets include:
  - SNS notifications.
  - EC2 actions (e.g., stop, terminate, or recover).
  - Autoscaling actions.

### CloudWatch Alarms – Composite Alarms
- Combine multiple alarms into a single alarm.
- Reduce alarm noise and monitor overall system health.

### EC2 Instance Recovery
- Automatically recovers EC2 instances using predefined alarm actions.

### CloudWatch Alarm: Good to Know
- Alarms can monitor high-resolution metrics with granularity up to 1 second.

---

## Amazon EventBridge
- **Type:** Event-driven architecture service.
- **Key Features:**
  - Routes events from AWS services or custom applications to targets.
  - Supports schema discovery for easier event integration.

### Amazon EventBridge Rules
- Define rules to filter and route events to specific targets.
- Example: Trigger a Lambda function on S3 object creation.

### Amazon EventBridge – Schema Registry
- Stores event schemas for discovery and integration.

### Amazon EventBridge – Resource-based Policy
- Grants cross-account access to EventBridge resources.

---

## CloudWatch Insights and Operational Visibility
### CloudWatch Container Insights
- Provides monitoring for containerized environments like ECS, EKS, and Kubernetes.
- Tracks metrics like CPU, memory usage, and pod performance.

### CloudWatch Lambda Insights
- Monitors Lambda functions' performance and resource utilization.

### CloudWatch Contributor Insights
- Identifies top contributors to system performance issues.

### CloudWatch Application Insights
- Automatically detects and analyzes problems in application resources.

---

## AWS CloudTrail
- **Type:** Audit service for API calls.
- **Key Features:**
  - Tracks API activity across AWS accounts.
  - Provides governance, compliance, and operational auditing.

### CloudTrail Diagram
- Visualize the flow of API activity logging and monitoring.

### CloudTrail Events
- **Management Events:** Track changes to resources (e.g., IAM, S3).
- **Data Events:** Monitor S3 object-level and Lambda function-level access.

### CloudTrail Insights
- Detects unusual operational activity.

### CloudTrail Events Retention
- Default retention: 90 days. Extend retention by exporting logs to S3.

### Amazon EventBridge + CloudTrail
- Integrate to react to specific API activities or anomalies.

---

## AWS Config
- **Type:** Configuration management and compliance monitoring service.
- **Key Features:**
  - Tracks resource configuration changes.
  - Enforces compliance with predefined rules.

### Config Rules
- Evaluate compliance with organizational policies (e.g., S3 bucket encryption).

### AWS Config Resource
- Tracks metadata and relationships of AWS resources.

### Config Rules – Remediations
- Automates remediation actions for non-compliant resources.

### Config Rules – Notifications
- Sends notifications via SNS for compliance changes.

---

## CloudWatch vs CloudTrail vs Config
### For an Elastic Load Balancer (ELB):
- **CloudWatch:** Monitors metrics like request count, latency, and error rates.
- **CloudTrail:** Logs API calls for ELB configuration changes.
- **Config:** Tracks ELB resource configurations and compliance with rules.
