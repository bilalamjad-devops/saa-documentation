
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


### 🏨 Hotel Room ki Misal (The Core Concept)

Farz karein aap ne Lahore jana hai aik bohot baray software exhibition ke liye, jahan poore Pakistan se log aa rahe hain. Ab aap ke paas room book karne ke 4 tareeqay hain:

1. **On-Demand (Normal Walk-in):** Aap direct hotel pohnche aur counter par kaha, *"Mujhe aik room chahiye."* Agar room khali hoa toh mil jayega, aur aap per-night ke hisab se poore paise de denge. Lekin agar exhibition ki wajah se hotel full hoa, toh aap ko room **nahi milega** (Capacity issue).
2. **On-Demand Capacity Reservation:** Aap ne hotel ko phone kiya aur kaha, *"28 June ko room no. 302 mere liye reserve rakhna, main raat 10 baje aao ga aur subah 3 baje chala jao ga."* Hotel aap se sirf un hours ka rent lega, lekin room aap ke liye **100% guarantee** save rahega. Koi aur wahan nahi ruk sakta.
3. **Zonal Reserved Instance (1-Year Contract for Room 302):** Aap ne hotel se 1 saal ka contract kar liya ke *"Room number 302 poora saal mera hai."* Is lambay contract ki wajah se hotel aap ko **heavy discount** de dega, lekin aap wahan sirf 5 ghante rukein ya na rukein, rent poore saal ka dena parega.
4. **Regional Reserved Instance (Discount Voucher for the whole Hotel Chain):** Hotel ka maalik aap ko aik discount coupon de deta hai ke *"Aap hamari Lahore branch mein kisi bhi floor par room lein, aap ko 40% discount milega. Lekin hum pehle se koi specific room reserve nahi karenge, jo khali mila wahan discount chal jayega."* (Discount hai, par room ki guarantee nahi).

---
