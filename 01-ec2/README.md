
1. Question

Category: CSAA – Design Cost-Optimized Architectures

A multinational corporate and investment bank regularly processes steady workloads of accruals, loan interests, and other critical financial calculations every night from 10 PM to 3 AM on their on-premises data center for their corporate clients. Once the process is done, the results are then uploaded to the Oracle General Ledger which means that the processing should not be delayed or interrupted. The CTO has decided to move its IT infrastructure to AWS to save costs. The company needs to reserve compute capacity in a specific Availability Zone to properly run their workloads.

As the Senior Solutions Architect, how can you implement a cost-effective architecture in AWS for their financial system?


- Use On-Demand EC2 instances which allows you to pay for the instances that you launch and use by the second. Reserve compute capacity in a specific Availability Zone to avoid any interruption.
- Use Regional Reserved Instances to reserve capacity on a specific Availability Zone and lower the operating cost through its billing discounts.
- Use Dedicated Hosts, which provide a physical host that is fully dedicated to running your instances, and bring your existing per-socket, per-core, or per-VM software licenses to reduce costs.
- Use On-Demand Capacity Reservations, which provide compute capacity that is always available on the specified recurring schedule.


When a critical workload runs for short daily windows but requires **guaranteed capacity** in a specific Availability Zone (AZ) without interruptions:

*   ❌ **On-Demand (Standard):** Risk of capacity unavailability during peak hours. No capacity reservation.
*   ❌ **Regional RIs:** Provides billing discounts across the region, but **does NOT guarantee capacity** in a specific AZ.
*   ❌ **Dedicated Hosts:** Too expensive and highly underutilized for a 5-hour workload.
*   ✅ **On-Demand Capacity Reservations:** Guarantees capacity in a specific AZ with **no term commitment** (1/3 years). Can be programmatically created before 10 PM and canceled after 3 AM to minimize costs.
