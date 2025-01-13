# AWS Serverless Solutions Architecture

## Task: Build a Mobile Application
### Requirements:
1. Expose as REST API with HTTPS.
2. Serverless architecture.
3. Users should directly interact with their own folder in Amazon S3.
4. Users authenticate via a managed serverless service.
5. Users can write and read to-dos, but mostly read them.
6. Database should scale and support high read throughput.

---

## Solution Architecture Steps

### 1. Expose as REST API with HTTPS
- **Use Amazon API Gateway**:
  - Create a REST API with HTTPS endpoints.
  - Enable CORS to allow mobile clients to interact with the API.
  - Use stages (e.g., dev, test, prod) for deployment.

### 2. Implement Serverless Architecture
- **Use AWS Lambda**:
  - Write backend logic using Lambda functions.
  - Functions are triggered by API Gateway.
  - Automatically scale based on incoming requests.

### 3. Enable Direct S3 Interaction
- **Use Amazon S3**:
  - Create an S3 bucket for user data.
  - Structure folders by user (e.g., `s3://myapp/user-id/`).
  - Use pre-signed URLs for secure upload and download operations.

### 4. Authenticate Users with a Managed Service
- **Use Amazon Cognito**:
  - Set up a Cognito User Pool for user authentication.
  - Enable OAuth 2.0 for token-based authentication.
  - Use Cognito Identity Pools to provide temporary AWS credentials for S3 access.

### 5. Manage User To-Dos
- **Database Selection**:
  - Use Amazon DynamoDB:
    - NoSQL database with seamless scaling.
    - High read throughput to accommodate frequent read operations.
- **Data Structure**:
  - Design tables with primary keys and indexes to support user-specific queries (e.g., `PK = user-id`, `SK = todo-id`).

### 6. Optimize Database for High Read Throughput
- **Provisioned Throughput**:
  - Use DynamoDB on-demand mode for automatic scaling.
  - If predictable, configure provisioned capacity with high read throughput.
- **Enable DynamoDB Accelerator (DAX)**:
  - Cache frequently accessed data.
  - Reduce latency for read operations.

---

## Example Workflow

1. **User Authentication**:
   - Users sign up and log in via the mobile app using Cognito.
   - Cognito issues tokens (ID, Access, Refresh).

2. **Access Control**:
   - Mobile app requests pre-signed URLs for S3 folder operations via API Gateway.
   - Lambda validates user permissions using Cognito tokens.

3. **Manage To-Dos**:
   - Write requests trigger Lambda functions to store to-dos in DynamoDB.
   - Read requests retrieve to-dos with optimized queries and DAX caching.

4. **Secure Data Transfer**:
   - All interactions use HTTPS.
   - S3 operations use pre-signed URLs with limited permissions and expiration.

---

## Benefits of the Architecture
- **Serverless**:
  - Reduces operational overhead.
  - Scales automatically based on user demand.
- **Secure**:
  - Cognito ensures robust user authentication.
  - Pre-signed URLs secure S3 operations.
- **Cost-Efficient**:
  - Pay only for what you use (API Gateway, Lambda, DynamoDB).
- **High Performance**:
  - DynamoDB and DAX ensure fast and scalable data access.

---

## Diagram
### High-Level Architecture
1. **Frontend**: Mobile app.
2. **API Gateway**: Exposes REST API.
3. **Lambda**: Backend logic.
4. **Cognito**: User authentication and access control.
5. **S3**: User-specific folder storage.
6. **DynamoDB**: To-Do storage with DAX caching.

This architecture ensures scalability, security, and cost-efficiency, meeting the application's requirements effectively.

