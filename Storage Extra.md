# AWS Storage Extra

## AWS Snow Family
The AWS Snow Family is a collection of physical devices and edge computing solutions designed to securely transfer large amounts of data to and from AWS.

### Data Migrations with AWS Snow Family
AWS Snow Family helps move data ranging from terabytes to petabytes securely into AWS using physical devices when network transfers are impractical.

### Snowball Edge (for data transfers)
Snowball Edge devices are data transfer and edge computing devices that:
- Transfer terabytes or petabytes of data.
- Provide edge computing capabilities for processing data locally.

#### Snowball Edge Types:
1. **Snowball Edge Storage Optimized**:
   - High-capacity storage for data transfer and local processing.
   - Suitable for advanced data processing.
2. **Snowball Edge Compute Optimized**:
   - Enhanced compute capabilities for machine learning, video processing, and analytics.

### AWS Snowcone & Snowcone SSD
- **Snowcone**:
  - Smallest member of the Snow Family.
  - Lightweight and rugged, ideal for edge locations with limited space.
- **Snowcone SSD**:
  - Provides additional storage with SSD for faster data transfer and retrieval.

### AWS Snowmobile
AWS Snowmobile is an exabyte-scale data transfer service using a secure, 45-foot-long shipping container pulled by a truck. Suitable for extremely large-scale data migrations.

### AWS Snow Family for Data Migrations
1. **Data Collection:** Use Snow Family devices to collect data at edge locations.
2. **Transfer:** Securely ship devices to AWS for data ingestion.
3. **Processing:** Optionally process data at the edge before transferring it.

### Snow Family – Usage Process
1. Request a Snow device via the AWS Management Console.
2. Load data onto the device.
3. Ship the device back to AWS.
4. AWS ingests the data into the specified AWS storage services.

## Edge Computing
### What is Edge Computing?
Edge computing involves processing data near its source rather than relying on a central location, reducing latency and bandwidth usage.

### Snow Family – Edge Computing
Snow Family devices enable edge computing by allowing local data processing, filtering, and analysis before transferring to the cloud.

### AWS OpsHub
AWS OpsHub is a graphical user interface for managing Snow Family devices. It simplifies:
- Device setup.
- Data transfer.
- Monitoring and management.

### Solution Architecture: Snowball into Glacier
Use Snowball devices to transfer large amounts of archival data into Amazon S3 Glacier for cost-effective long-term storage.

## Amazon FSx
Amazon FSx offers fully managed file storage built for specific workloads.

### Amazon FSx for Windows (File Server)
- Provides fully managed Windows File Server storage.
- Supports SMB protocol for seamless integration with Windows applications.
- Ideal for file-based workloads such as user shares and application data.

### Amazon FSx for Lustre
- High-performance file system optimized for compute-intensive workloads like machine learning and analytics.
- Integrates with Amazon S3 to process S3 objects directly.

#### FSx Lustre - File System Deployment Options:
1. Persistent storage for long-term workloads.
2. Scratch storage for temporary, high-performance workloads.

### Amazon FSx for NetApp ONTAP
- Fully managed storage service providing NetApp ONTAP file systems.
- Ideal for applications requiring advanced data management capabilities.

### Amazon FSx for OpenZFS
- Fully managed OpenZFS file systems.
- Designed for performance-intensive applications needing advanced storage features like snapshots and clones.

## Hybrid Cloud for Storage
Combining on-premises storage solutions with AWS storage services to provide a hybrid cloud environment.

## AWS Storage Cloud Native Options
- **Amazon S3**: Object storage for a wide range of use cases.
- **Amazon EBS**: Block storage for EC2 instances.
- **Amazon EFS**: Scalable file storage for use with AWS Cloud services.

## AWS Storage Gateway
AWS Storage Gateway connects on-premises environments to AWS, enabling hybrid cloud storage.

### Amazon S3 File Gateway
- Provides on-premises applications with access to virtually unlimited cloud storage.
- Caches frequently accessed data locally for low-latency access.

### Amazon FSx File Gateway
- Enables on-premises applications to access Amazon FSx file systems.

### Volume Gateway
- Provides block storage via iSCSI, with backups stored in AWS.
- Supports snapshots to Amazon S3.

### Tape Gateway
- Virtual tape library for cost-effective and scalable tape backup to the cloud.

### Storage Gateway – Hardware Appliance
- Physical appliance for environments without existing virtualized infrastructure.

## AWS Transfer Family
Managed file transfer service supporting protocols like SFTP, FTPS, and FTP for seamless migration of files into AWS.

## AWS DataSync
Service for automating data transfer between on-premises storage and AWS.

### AWS DataSync NFS / SMB to AWS
- Supports NFS and SMB protocols for moving data into AWS storage services like S3 and EFS.

### AWS DataSync Transfer between AWS storage services
- Allows data transfer between S3, EFS, and FSx file systems within AWS.

## Storage Comparison
| Feature             | Amazon S3         | Amazon EBS      | Amazon EFS      |
|---------------------|-------------------|-----------------|-----------------|
| Type                | Object storage    | Block storage   | File storage    |
| Use Case            | Backup, archives | Databases       | Shared file systems |
| Durability          | 99.999999999%    | High            | High            |
| Scalability         | Virtually unlimited | Up to 16 TiB/volume | Scalable       |

