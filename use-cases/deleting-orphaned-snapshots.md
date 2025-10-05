## Use Case 5: Deleting Orphaned Snapshots

**Scenario:** A software development company uses Azure Blob Storage to store virtual machine disks (VHDs). They regularly create snapshots of these disks for backup purposes. Over time, many of these snapshots become orphaned (the original VHD is deleted, but the snapshot remains), consuming unnecessary storage space and incurring costs.

**Solution using Azure Storage Actions:**

*   **Storage Task: Delete Orphaned Snapshots**
    *   **Condition:**
        *   `Blob type` is `Snapshot`.
        *   `Parent blob` `does not exist`.
    *   **Operation:**
        *   `Delete blob`.
    *   **Assignment:**
        *   This task is assigned to the storage account containing the VHDs and is scheduled to run monthly to clean up orphaned snapshots.

This helps the company maintain a clean and cost-effective storage environment by automatically removing unnecessary snapshots.
