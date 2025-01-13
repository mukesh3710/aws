# AWS Data & Analytics Overview

## Amazon Athena
- **Type:** Interactive query service.
- **Key Features:**
  - Analyze data stored in Amazon S3 using standard SQL.
  - Serverless and pay-per-query pricing.
- **Use Cases:** Ad hoc analysis, querying log data, and quick data insights.

### Amazon Athena – Performance Improvement
- Partition data in S3 for faster queries.
- Convert data to columnar formats like Parquet or ORC.
- Use **optimized table formats** like Apache Iceberg for transaction-level operations.
- Reduce the amount of data scanned using projection and filtering.

### Amazon Athena – Federated Query
- Query data from various sources (e.g., DynamoDB, RDS, or on-prem databases).
- Leverages Athena data source connectors to integrate with external systems.
- Supports unified analysis across multiple datasets.

---

## Amazon Redshift

### Redshift Overview
- **Type:** Fully managed data warehouse service.
- **Key Features:**
  - Designed for analytics workloads.
  - Supports petabyte-scale data.
  - Integrates with BI tools and AWS analytics services.

### Redshift Cluster
- Comprises leader nodes (query optimization) and compute nodes (query execution).
- Supports **RA3** instances for scalability and cost-efficiency.

### Redshift – Snapshots & DR
- Automated and manual snapshots for backups.
- Supports cross-region snapshots for disaster recovery (DR).

### Loading Data into Redshift
- Large inserts perform better than small ones due to reduced overhead.
- Use COPY command to load data efficiently from S3 or DynamoDB.

### Redshift Spectrum
- Enables querying data in S3 without loading it into Redshift.
- Use cases: Extending analytics to large, external datasets.

---

## Amazon OpenSearch Service
- **Type:** Managed search and analytics engine.
- **Use Cases:** Application search, log analytics, and observability.

### OpenSearch Patterns
#### DynamoDB
- Stream data from DynamoDB to OpenSearch using **DynamoDB Streams** and **Lambda**.

#### CloudWatch Logs
- Stream logs to OpenSearch via **CloudWatch Log Subscriptions** and **Lambda**.

#### Kinesis Data Streams & Kinesis Data Firehose
- Use Firehose to batch, transform, and load data into OpenSearch.

---

## Amazon EMR
- **Type:** Managed Hadoop and Spark framework.
- **Use Cases:** Big data processing, machine learning, and data transformation.

### EMR – Node Types & Purchasing
- **Node Types:**
  - Master Node: Manages cluster.
  - Core Node: Processes and stores data.
  - Task Node: Processes data without storage.
- **Purchasing Options:** Spot instances for cost savings or On-Demand for stability.

---

## Amazon QuickSight
- **Type:** BI service for interactive dashboards.
- **Key Features:**
  - Integration with AWS data services.
  - Embeddable dashboards.

### QuickSight Integrations
- Connects to Redshift, Athena, S3, and more.
- Supports SPICE for in-memory acceleration.

### QuickSight – Dashboard & Analysis
- Create visualizations and perform analysis with drag-and-drop interface.
- Share insights via dashboards and reports.

---

## AWS Glue
- **Type:** ETL service.
- **Key Features:**
  - Automates data discovery, transformation, and cataloging.

### Glue – Convert Data into Parquet Format
- Optimize S3 storage by converting raw data to **Parquet** for efficient querying.

### Glue Data Catalog
- Centralized metadata store for datasets across AWS services.

### Glue – Things to Know
- Serverless and scalable ETL.
- Integrated with Athena, Redshift, and Lake Formation.

---

## AWS Lake Formation
- Simplifies creation and management of secure data lakes.
- Centralized permissions for cross-service data access.

### Lake Formation Centralized Permissions Example
- Define fine-grained access policies for Athena, Redshift, and EMR.

---

## Kinesis Data Analytics
- Real-time data processing for SQL applications and Apache Flink.

### Kinesis Data Analytics for SQL Applications
- Analyze streaming data using SQL.
- Integrate with Kinesis Data Streams or Firehose.

### Kinesis Data Analytics for Apache Flink
- Build advanced streaming applications using Flink’s APIs.

---

## Amazon Managed Streaming for Apache Kafka (MSK)
- **Type:** Managed Apache Kafka service.
- **Use Cases:** Real-time data ingestion and processing.

### Apache Kafka at a High Level
- Publish-subscribe messaging pattern for event streaming.
- Handles real-time event pipelines and log processing.

### Kinesis Data Streams vs. Amazon MSK
- **Kinesis:** Fully managed, serverless.
- **MSK:** Managed Kafka clusters with more control.

### Amazon MSK Consumers
- Tools for consuming Kafka data: Lambda, Kinesis, or custom applications.

---

## Big Data Ingestion Pipeline
- Combine services like Kinesis, MSK, Glue, and Redshift for scalable data ingestion.

### Big Data Ingestion Pipeline Discussion
- Use **Kinesis Firehose** for real-time streaming into data lakes.
- Implement ETL pipelines with Glue for data transformation.
- Store processed data in Redshift or S3 for analytics.
