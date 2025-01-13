# AWS Databases Overview

## Databases in AWS
AWS provides a comprehensive portfolio of purpose-built databases, enabling developers to build highly scalable and performance-optimized applications. Each database service is tailored for specific use cases and workload requirements.

---

## Choosing the Right Database
When selecting a database, consider:
- **Workload Type:** Transactional, analytical, or real-time.
- **Data Model:** Relational, key-value, document, graph, or time-series.
- **Scalability Needs:** On-demand or provisioned.
- **Latency Requirements:** Milliseconds, sub-milliseconds, or batch processing.
- **Durability and Availability:** Required uptime and data retention policies.

---

## Database Types
- **Relational Databases:** Structured data with predefined schema.
- **Key-Value Stores:** Simple, scalable, and optimized for high-speed lookups.
- **Document Databases:** Flexible schema, ideal for hierarchical data.
- **Graph Databases:** Efficiently handle relationships between data.
- **In-Memory Databases:** High-speed, low-latency data processing.
- **Time-Series Databases:** Optimized for time-stamped data.
- **Ledger Databases:** Immutable records with cryptographic verification.

---

## AWS Database Services Summary

### Amazon RDS – Summary
- **Type:** Managed Relational Database.
- **Key Features:**
  - Supports multiple engines: MySQL, PostgreSQL, MariaDB, SQL Server, Oracle.
  - Automated backups, snapshots, and patch management.
  - Scalability with read replicas and multi-AZ deployments.

### Amazon Aurora – Summary
- **Type:** Relational Database (MySQL and PostgreSQL compatible).
- **Key Features:**
  - High-performance managed relational database.
  - Up to 5x faster than standard MySQL and 3x faster than PostgreSQL.
  - Fault-tolerant distributed storage with 6 copies of data across 3 AZs.

### Amazon ElastiCache – Summary
- **Type:** In-Memory Database.
- **Key Features:**
  - Supports Redis and Memcached.
  - Sub-millisecond latency for real-time applications.
  - Ideal for caching, session stores, and analytics.

### Amazon DynamoDB – Summary
- **Type:** NoSQL Key-Value Store.
- **Key Features:**
  - Fully managed, serverless database with single-digit millisecond latency.
  - On-demand and provisioned capacity modes.
  - Supports global tables for multi-region replication.

### Amazon S3 – Summary
- **Type:** Object Storage.
- **Key Features:**
  - Scalability, durability, and availability for storing unstructured data.
  - Integrates with analytics and big data tools.
  - Versioning, encryption, and lifecycle management.

---

## Specialized Databases

### Amazon DocumentDB
- **Type:** Managed Document Database (MongoDB compatible).
- **Key Features:**
  - Built for JSON-like document storage.
  - Scales horizontally with replica sets.
  - Automated backups and fault tolerance.

### Amazon Neptune
- **Type:** Graph Database.
- **Key Features:**
  - Supports property graph and RDF models.
  - Optimized for querying relationships in data.
  - Ideal for recommendation engines, fraud detection, and knowledge graphs.

### Amazon Keyspaces (for Apache Cassandra)
- **Type:** Managed NoSQL Database.
- **Key Features:**
  - Compatible with Apache Cassandra APIs.
  - Fully managed, serverless, and scalable.
  - High availability across multiple AZs.

### Amazon QLDB
- **Type:** Ledger Database.
- **Key Features:**
  - Immutable and cryptographically verifiable.
  - Tracks all changes to application data.
  - Ideal for financial systems, supply chains, and compliance.

### Amazon Timestream
- **Type:** Managed Time-Series Database.
- **Key Features:**
  - Optimized for IoT and operational applications.
  - Stores trillions of time-series data points.
  - Supports advanced queries with SQL-like syntax.

### Amazon Timestream – Architecture
- **Storage Layer:** Separates hot and cold data automatically.
- **Query Engine:** Optimized for time-series queries and aggregations.
- **Integration:** Seamless with AWS IoT Core, CloudWatch, and analytics tools.

---
