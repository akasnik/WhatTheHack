# Challenge 3: Add Branch File Server as a new server endpoint - Coach's Guide

[< Previous Challenge](./02-server_endpoints.md) - **[Home](./README.md)** - [Next Challenge >](./04-add_data_protection.md)

## Notes and Guidance


## Solution Guide
Config Branch File Server (no file shares) to replicate/sync the files from Azure Files. The idea is to have a local cache of often/recently accessed (hot) files in branch file server for branch users. Configure cloud tiering policy.

1. Create a folder 'F:\HQ-BR_Share' in Branch File Server (vm-branch1-fs-1)

2. Deploy Azure File Sync Agent

3. Register Branch File Server with Storage Sync Service

4. Add Branch File Server 'F:\HQ-BR_Share' as a new server endpoint to existing Sync Group.
    - Server endpoint config:
        - Registered Server: vm-branch1-fs-1.contoso.com
        - Path: F:\HQ-BR_Share
        - **[Cloud Tiering](https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-cloud-tiering-overview)**: Enabled
            - Volume Free Space Policy: 20 (default)
            - Date Policy: Enabled, 7 days
        - Initial Download: Recall the namespace only
        - For more info refer **[Sync policies that affect cloud tiering](https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-cloud-tiering-overview#sync-policies-that-affect-cloud-tiering)**.
        - **[Offline Data Transfer](https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-offline-data-transfer)**: Disabled
    - Follow https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-files-server-endpoint