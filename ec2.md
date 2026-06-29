



# AWS EC2 Capacity & Cost Optimization Notes

## 🎯 Scenario: Short-Duration Critical Nightly Workloads (e.g., 10 PM - 3 AM)
When a critical workload runs for short daily windows but requires **guaranteed capacity** in a specific Availability Zone (AZ) without interruptions:

*   ❌ **On-Demand (Standard):** Risk of capacity unavailability during peak hours. No capacity reservation.
*   ✅ **On-Demand Capacity Reservations:** Guarantees capacity in a specific AZ with **no term commitment** (1/3 years). Can be programmatically created before 10 PM and canceled after 3 AM to minimize costs.
*   ❌ **Regional RIs:** Provides billing discounts across the region, but **does NOT guarantee capacity** in a specific AZ.
*   ❌ **Dedicated Hosts:** Too expensive and highly underutilized for a 5-hour workload.


---

## 🎯 Scenario: Script/Automation Fails After Launching a Certain Number of Instances
When automated scripts (Python/Boto3, Terraform) stop provisioning instances halfway and throw errors, it is usually due to AWS Service Quotas.

*   ❌ **The Misconception:** AWS has a flat limit of 20 total instances.
*   ✅ **The Reality:** AWS enforces a **vCPU-based On-Demand Instance limit per Region** (Standard vCPU quota). Once your running instances exhaust the allowed total number of vCPUs for that region, subsequent API requests fail.
*   🛠️ **How to Resolve:** Navigate to the **AWS Service Quotas** dashboard, select the specific instance type group (e.g., Running On-Demand Standard instances), and submit a **Limit Increase Request**. Once AWS approves it, rerun the script.
*   📌 **Exam Tip:** Service quotas and limits are bound **Per Region**, not per Availability Zone (AZ). Changing the AZ within the same region will NOT fix a vCPU limit error.


---


## 🎯 Scenario: Monitoring EC2 Performance Metrics via Amazon CloudWatch
Understanding the boundaries between AWS Default Metrics and Custom Metrics is crucial for both operational setups and the SAA-C03 exam.

### 🟢 Default Metrics (Hypervisor-Level)
Available out-of-the-box. AWS monitors these from the outside of the virtual machine without needing any internal access:
*   `CPUUtilization`
*   `DiskReadOps` / `DiskWriteOps` (I/O Activity)
*   `NetworkIn` / `NetworkOut` (Network Throughput)

### 🔴 Custom Metrics (OS-Level - Requires CloudWatch Agent)
AWS cannot see inside the Operating System due to security boundaries. The following metrics require manual setup via the CloudWatch Agent or scripts:
*   **Memory Utilization (RAM)** ⚠️ *[Most Asked]*
*   Disk Space Utilization (Available vs Used storage inside the OS)
*   Disk Swap Utilization
*   Application Logs

📌 **Exam Tip:** Whenever a scenario mentions monitoring **Memory/RAM** or **internal disk space percentages**, the correct architectural answer must involve installing the **CloudWatch Agent**.
