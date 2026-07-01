## 🎯 Scenario: Optimizing Serverless Microservices for Millions of Concurrent Users (Mobile AR Game)
When scaling serverless backends powered by API Gateway, Lambda, and DynamoDB, architectural performance bottlenecks usually occur at the database or ingress tier.

### ⚙️ Core Optimization Strategies:
1.  **In-Memory Acceleration via DynamoDB Accelerator (DAX):** Moves read latency from milliseconds to microseconds. It reduces costs significantly by offloading heavy, repetitive read traffic from the underlying DynamoDB table storage.
2.  **API Gateway Edge Caching:** Caches API responses at the API Gateway level. It prevents unnecessary downstream AWS Lambda invocations, resulting in major cost savings and lightning-fast frontend responses.

### ⚠️ Technical Traps to Remember:
*   **The CLI Default behavior:** Tables created via the standard AWS CLI do **NOT** have Auto Scaling enabled by default. You must explicitly configure and ensure Auto Scaling parameters (scaling limits for RCU/WCU) are turned on manually.
*   **CloudFront Incompatibility:** Amazon CloudFront cannot accept a DynamoDB table directly as an operational Origin target.

📌 **Exam Rule of Thumb:** For high-throughput global applications requiring microsecond database performance, couple **DynamoDB + DAX**. To save serverless compute fees, always turn on **API Gateway Caching** to intercept redundant traffic before it hits Lambda.
