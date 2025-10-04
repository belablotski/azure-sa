# Cost of Azure Storage Actions

The cost model for Storage Actions is multi-faceted. It's not a single flat fee; rather, it's based on what you do and how much data you process. There are two main categories of costs:

### 1. Storage Actions Service Charges
This is the cost for using the service itself, broken down into three meters:

*   **Task Execution Instance Charge:** You are charged a small, flat fee for *each time a task assignment runs*. If you have a task scheduled to run daily, you will incur this charge every day.
*   **Objects Targeted Charge:** This is a charge based on the number of objects (blobs) that are *scanned and evaluated* against your task's conditions. This is typically priced per million objects.
*   **Operations Performed Charge:** This is a charge for each action (e.g., setting a tag, deleting a blob) that is successfully executed on an object that met your conditions. This is also typically priced per million operations.

### 2. Downstream Azure Storage Costs
This is a crucial and often overlooked cost. The operations performed by a Storage Action are simply API calls to the storage account, and these API calls have their own standard transaction costs.

*   **Example:** If your Storage Action applies an immutability policy to 100,000 blobs, you will be billed by the Storage Actions service for 100,000 "operations performed," AND you will be billed by Azure Storage for the cost of 100,000 "Set Blob Immutability Policy" write operations.

### Key Takeaway on Cost
The most significant factor in your cost is the **Objects Targeted Charge**. To manage costs effectively, you should make your conditions as specific as possible using path prefixes to minimize the number of blobs that need to be scanned during each run.
