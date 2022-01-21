# Challenge 1: Setup Azure Files and File Sync Service - Coach's Guide

[< Previous Challenge](./00-lab_setup.md) - **[Home](./README.md)** - [Next Challenge >](./02-server_endpoints.md)

## Notes and Guidance


## Solution Guide

Create Azure Files share, setup and config Storage Sync Service.

1. Create an Azure Storage account and file share
    - Select 'transaction optimized' tier as thats most cost effective during initial sync/migration. During production deployment, its suggested to start with transaction optimized and switch to the right **[storage tier](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-planning#storage-tiers)** - Cool/Hot/Transaction Optimized after reviewing the workload use case, data churn pattern/transaction units, data size and bill.
    - Follow https://docs.microsoft.com/en-us/azure/storage/files/storage-how-to-create-file-share?tabs=azure-portal

2. Deploy Azure File Sync service from marketplace (aka Storage Sync Service)
    - Follow https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-files-extend-servers#deploy-the-service

3. Deploy Azure File Sync Agent on HQ File Server (vm-hq-fs-1)
    - Use Azure Bastion to connect to the VM
    - Install Azure Az powershell module (Note: already deployed in lab VM via DSC) 
    - Use Edge browser to download the Azure File Sync Agent.
    - For download link and instructions, follow https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-files-extend-servers#install-the-agent

4. Register HQ File Server with Storage Sync Service
    - Follow https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-files-deployment-guide?tabs=azure-portal%2Cproactive-portal#register-windows-server-with-storage-sync-service
    - Go to Storage Sync Service, under Sync > Registered Servers. Validate if you can see the HQ file server (vm-hq-fs-1) with Online state.

5. Create a Sync Group with a Cloud Endpoint (Azure files storage)
    - Follow https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-files-deployment-guide?tabs=azure-portal%2Cproactive-portal#create-a-sync-group-and-a-cloud-endpoint