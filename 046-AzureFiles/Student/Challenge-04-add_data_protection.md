# Challenge 4: Enable Data Protection - Snapshot or Azure Backup

[< Previous Challenge](./Challenge-03-add_branch_file_server.md) - **[Home](../README.md)** - [Next Challenge >](./Challenge-05-secure_private_endpoint.md)

## Pre-requisites

- Deployment of environment described in [Challenge 0](./Challenge-00-lab_setup.md) should be completed and validated.
- Azure Files deployed in Challenge 1 should be deployed and have some files.

## Introduction

Azure File offers protection with Azure File snapshots. Those can be managed manually/programaticaly or  by integration with Azure Recovery Services Vault where snapshots are created based on Backup policy you configure. Note that at time of writing this document snapshots were still stored on same File share and there is no option to store snapshots in Recovery Services Vault.

## Description

1. Azure File snapshot management:
    - In Azure portal, examine snapshots user interface for File share you created
    - Take a manual snapshot
    - Modify a file on HQ File server and wait for synchronization to Azure File share completes
    - Through Azure portal user interface for managing snapshots restore earlier version of file you modified
    - On Azure File share check if file content was restored to previous version
1. Azure Backup integration:
    - Create a Recovery Services Vault in same region as your Azure File resources are
    - Configure Backup for your Azure File share
    - Run an on-demand backup job (Backup Now)
    - After Backup operation completes, delete few Files and/or Folders from HQ File server
    - Use Azure Backup to restore Files and Folders to original location


## Success Criteria

At the end of this challenge you should have your Azure File share protected and be able to restore from previous versions.

## Learning Resources
- [Overview of share snapshots for Azure Files](https://docs.microsoft.com/en-us/azure/storage/files/storage-snapshots-files)
- [Back up Azure file shares](https://docs.microsoft.com/azure/backup/backup-afs)

## Tips
- Azure FileSync supports also integration with Previous versions feature on Windows server. You can try this by right clicking on File in Windows Explorer, going to properties and select Previous Versions tab.