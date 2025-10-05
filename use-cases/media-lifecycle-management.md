## Use Case 2: Data Lifecycle Management for a Media Company

**Scenario:** A media company stores large video files in Azure Blob Storage. To optimize costs, they want to move video files that haven't been accessed in the last 90 days to the Cool storage tier. If a video is still not accessed for another 90 days, it should be moved to the Archive tier.

**Solution using Azure Storage Actions:**

1.  **Storage Task 1: Move to Cool Tier**
    *   **Condition:**
        *   `Last access time` is `older than 90 days`.
        *   `Blob tier` is `Hot`.
    *   **Operation:**
        *   `Set blob tier` to `Cool`.
    *   **Assignment:**
        *   This task is assigned to the storage account containing the video files and is scheduled to run weekly.

2.  **Storage Task 2: Move to Archive Tier**
    *   **Condition:**
        *   `Last access time` is `older than 180 days`.
        *   `Blob tier` is `Cool`.
    *   **Operation:**
        *   `Set blob tier` to `Archive`.
    *   **Assignment:**
        *   This task is also assigned to the same storage account and runs weekly.

This automated lifecycle management helps the media company significantly reduce storage costs for their large video library.
