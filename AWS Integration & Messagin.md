# AWS Integration & Messaging

## What’s a Queue?
A queue is a data structure used to store messages in a temporary, reliable, and sequential manner until they are processed. Queues allow for asynchronous communication between different parts of an application, decoupling the components.

---

## Amazon SQS – Standard Queue
### Features:
- **Unlimited Throughput**: Supports a nearly unlimited number of transactions per second.
- **At-least-once Delivery**: Messages are delivered at least once but may be delivered more than once.
- **Best-effort Ordering**: Order of messages is not guaranteed.

### SQS – Producing Messages
- Producers send messages to the SQS queue.
- Messages can include metadata and attributes.

### SQS – Consuming Messages
- Consumers retrieve messages from the queue using the `ReceiveMessage` API.
- After processing, messages must be deleted from the queue.

### SQS – Multiple EC2 Instances Consumers
- Multiple EC2 instances can poll and process messages simultaneously to increase throughput.

### SQS with Auto Scaling Group (ASG)
- Automatically scale the number of EC2 instances based on the number of messages in the SQS queue.

### SQS to Decouple Between Application Tiers
- SQS allows different tiers (e.g., front-end and back-end) to communicate asynchronously.

### Amazon SQS – Security
- Integration with AWS IAM to control access.
- Messages are encrypted in transit (SSL/TLS) and at rest (SSE).

### SQS – Message Visibility Timeout
- Defines the period during which a message is invisible to other consumers after being retrieved.
- Default: 30 seconds. Max: 12 hours.

### Amazon SQS – Long Polling
- Reduces cost and latency by waiting until a message arrives or the long polling timeout is reached.

---

## Amazon SQS – FIFO Queue
### Features:
- **First-In-First-Out**: Messages are processed in the exact order they are sent.
- **Exactly-once Processing**: Ensures messages are not duplicated.

### Use Cases:
- Financial transactions.
- Order processing systems.

---

## Amazon SNS
- A fully managed pub/sub messaging service.
- Allows publishers to send messages to multiple subscribers.

### SNS Integrates with Many AWS Services:
- S3, Lambda, SQS, CloudWatch, Kinesis, etc.

### Amazon SNS – How to Publish:
- Use AWS SDK, CLI, or AWS Console.

### Amazon SNS – Security:
- Supports encryption at rest and in transit.
- Access control via IAM policies.

### SNS + SQS: Fan Out
- Messages published to an SNS topic can be delivered to multiple SQS queues.

---

## Applications:
### S3 Events to Multiple Queues:
- Use S3 event notifications to publish to an SNS topic, which delivers to multiple SQS queues.

### SNS to Amazon S3 Through Kinesis Data Firehose:
- Route messages to an S3 bucket using Kinesis Data Firehose for data ingestion.

### Amazon SNS – FIFO Topic:
- Ensures message order and exactly-once delivery to subscribers.

### SNS FIFO + SQS FIFO: Fan Out:
- Combines SNS FIFO and SQS FIFO for ordered fan-out scenarios.

### SNS – Message Filtering:
- Subscribers can specify message filtering policies to receive only relevant messages.

---

## Kinesis Overview
- A platform for real-time data streaming and analytics.

### Kinesis Data Streams:
- Real-time ingestion of streaming data.
- Data stored in shards.

### Kinesis Data Streams – Capacity Modes:
- **On-demand**: Automatically scales to match throughput.
- **Provisioned**: Pre-defined read/write throughput.

### Kinesis Data Streams Security:
- IAM policies for access control.
- Encryption using KMS.

### Kinesis Data Firehose:
- A fully managed service for loading streaming data into data lakes, warehouses, and analytics services.

### Kinesis Data Streams vs Firehose:
- **Kinesis Data Streams**: Real-time, custom applications.
- **Firehose**: Fully managed, auto-scaling, no custom application required.

---

## Ordering Data:
### Ordering Data into Kinesis:
- Leverage partition keys to control the order within a shard.

### Ordering Data into SQS:
- Use FIFO queues to ensure order.

### Kinesis vs SQS Ordering:
- Kinesis provides ordering within a shard.
- SQS FIFO ensures strict ordering across the queue.

---

## SQS vs SNS vs Kinesis
- **SQS**: Queue-based, decouples producers and consumers.
- **SNS**: Pub/Sub model for broadcasting messages.
- **Kinesis**: Real-time streaming and analytics.

---

## Amazon MQ
- A managed message broker service for Apache ActiveMQ and RabbitMQ.
- Supports standard messaging protocols such as MQTT, AMQP, and STOMP.

### Amazon MQ – High Availability:
- Multi-AZ deployment for fault tolerance.
- Automatic failover to standby broker in case of failures.

