## Use Case 4: Data Hydration for Analytics

**Scenario:** A retail company archives its sales data in Azure Blob Storage. Periodically, the data analytics team needs to rehydrate a subset of this data to the Hot tier for analysis. The data to be rehydrated is identified by a specific blob index tag.

**Solution using Azure Storage Actions:**

*   **Storage Task: Rehydrate Archived Data**
    *   **Condition:**
        *   `Blob tag` `AnalyticsProject` `equals` `Q4-2025-Analysis`.
        *   `Blob tier` is `Archive`.
    *   **Operation:**
        *   `Set blob tier` to `Hot`.
    *   **Assignment:**
        *   This task is assigned to the storage account containing the sales data and is run on-demand by the data analytics team when they need to rehydrate the data.

This allows the analytics team to easily access the data they need without having to manually rehydrate each blob, saving them time and effort.
