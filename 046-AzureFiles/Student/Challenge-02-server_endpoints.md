# Challenge 2: Configure Server endpoint and file synchronization

[< Previous Challenge](./Challenge-01-set_files_and_filesync.md) - **[Home](../README.md)** - [Next Challenge >](./Challenge-03-add_branch_file_server.md)

## Pre-requisites
- Deployment of environment described in [Challenge 0](./Challenge-00-lab_setup.md) should be completed and validated.
- Azure File share and Storage Sync Service should be deployed and configured with Cloud Endpoint.

## Introduction
In this challenge you will configure HQ File server as Server endpoint and enable synchronization of files to Azure File share.

## Description

1. Deploy Azure File Sync Agent on HQ File Server (vm-hq-fs-1) and register HQ File Server with Storage Sync Service you deployed
1. Create a Server Endpoint for HQ File Server using data path 'F:\Share1' which has pre-created dummy data files. You can leave Cloud Tiering settings Disabled for now.
1. Wait for initial synchronization to finish. You can go to Sync group, and wait for  the server endpoint is in healthy state. It may take couple of minutes for initial sync to finish.
1. Go to Azure File Share and see whether the files from F:\Share1 are listed. Navigate through the folder structure and try accessing the files.
1. Connect to HQ Client VM (vm-hq-client-1), access mapped M: drive or share path \vm-hq-fs-1\Share1. Modify files (add folders, files or change content on an existing file) on Share1. The changes should be synchronized instantly on Azure File share.

## Success Criteria

At the end of this challenge you should have Azure File share and HQ File server synchronized and changes from HQ File share being replicated to Azure File share.

## Learning Resources

- [Install the Azure File Sync agent](https://docs.microsoft.com/azure/storage/file-sync/file-sync-deployment-guide#install-the-azure-file-sync-agent)
- [Register Windows Server with Storage Sync Service](https://docs.microsoft.com/azure/storage/file-sync/file-sync-deployment-guide#register-windows-server-with-storage-sync-service)
- [Cloud tiering overview](https://docs.microsoft.com/azure/storage/file-sync/file-sync-cloud-tiering-overview)

## Tips

- Use Azure Bastion to connect to the VM when deploying File Sync agent