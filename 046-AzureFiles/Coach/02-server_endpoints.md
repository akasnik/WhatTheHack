# Challenge 2: Configure Server endpoint and file synchronization - Coach's Guide

[< Previous Challenge](./01-set_files_and_filesync.md) - **[Home](./README.md)** - [Next Challenge >](./03-add_branch_file_server.md)

## Notes and Guidance


## Solution Guide
Create HQ File Server endpoint and configure cloud tiering.

1. Create a Server Endpoint for HQ File Server using data path 'F:\Share1' which has pre-created dummy data files.
    - Server endpoint config:
        - Registered Server: vm-hq-fs-1.contoso.com
        - Path: F:\Share1
        - **[Cloud Tiering](https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-cloud-tiering-overview)**: Disabled
        - Initial Download: Recall the namespace first (default option).
        - For more info refer **[Sync policies that affect cloud tiering](https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-cloud-tiering-overview#sync-policies-that-affect-cloud-tiering)**.
        - **[Offline Data Transfer](https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-offline-data-transfer)**: Disabled
    - For instructions, refer https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-files-deployment-guide?tabs=azure-portal%2Cproactive-portal#create-a-server-endpoint
    - Let file sync do the full upload to the Azure file share (cloud endpoint).
    - Azure File Sync runs a process to detect the files in the cloud before starting the initial sync. The time taken to complete this process varies depending on the various factors like network speed, available bandwidth, and number of files and folders. For the rough estimation in the preview release, detection process runs approximately at 10 files/sec. Hence, even if pre-seeding runs fast, the overall time to get a fully running system may be significantly longer when data is pre-seeded in the cloud.

2. Go to Sync group, if the server endpoint is in Pending (health) state, wait couple of mins and click refresh.The status will change to green check (healthy) and sync activity will say "Upload & Download".

3. Select the server endpoint (click on file server name) to see a detailed status like last completed sync sessions. A green Health column and a Files Not Syncing value of 0 indicate that sync is working as expected. 
    - After few mins, the sync activity will say "Upload" and show sync status (# files / data size remaining) with last sync timestamp.
    - If this is not the case, refer the troubleshooting article https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-files-troubleshoot?tabs=portal1%2Cazure-portal to check common sync errors and how to handle files that are not syncing.

4. Go to Azure File Share and see whether the data on F:\Share1 is listed. Navigate through the folder structure and try accessing the files.

5. Connect to HQ Client VM (vm-hq-client-1), access mapped M: drive or share path \\vm-hq-fs-1\Share1.

6. Modify files (add folders, files or change content on an existing file) on Share1. The changes should be synchronized immediately on Azure File share.

More info on Cloud tiering: https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-cloud-tiering-overview
