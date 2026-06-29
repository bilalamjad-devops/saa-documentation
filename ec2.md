



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
