# Challenge 1: Setup Azure Files and File Sync Service

[< Previous Challenge](./Challenge-00-lab_setup.md) - **[Home](../README.md)** - [Next Challenge >](./Challenge-02-server_endpoints.md)

## Pre-requisites
Deployment of environment described in [Challenge 0](./Challenge-00-lab_setup.md) should be completed and validated.

## Introduction
In this challenge you will create Azure File share, setup and configure Storage Sync Service. At the end of challenge you should have Azure File and Storage Sync service with Cloud endpoint set up. You will create a Server endpoint in the next challenge.

Learn more on Azure File Sync and its components by watching this [video](https://www.youtube.com/watch?v=Zm2w8-TRn-o).

## Description

1. Create an Azure Storage account and file share
1. Deploy Azure File Sync service from marketplace (aka Storage Sync Service)
1. Create a Sync Group with a Cloud Endpoint (Azure File share)

## Success Criteria

At the end of this challenge you should have Azure File share and Storage Sync Service successfuly deployed. You should also have Cloud Endpoint configured that represents your Azure File share.

## Learning Resources

- [Create an Azure File share](https://docs.microsoft.com/azure/storage/files/storage-how-to-create-file-share?tabs=azure-portal)
- [Deploy Azure File Sync](https://docs.microsoft.com/azure/storage/file-sync/file-sync-deployment-guide)
- [Tutorial: Deploy Azure File Sync](https://docs.microsoft.com/azure/storage/files/storage-sync-files-extend-servers#deploy-the-service)

## Tips

- Select 'transaction optimized' tier as it is the most cost effective SKU during initial sync/migration. During production deployment, it is suggested to start with transaction optimized and switch to the correct **[storage tier](https://docs.microsoft.com/azure/storage/files/storage-files-planning#storage-tiers)** - Cool/Hot/Transaction Optimized after reviewing the workload use case, data churn pattern/transaction units, data size and bill.
- When naming Storage Account that holds Azure File share, note that if in future you would want Azure File share to be domain joined for seamless AD authentication, it should have maximium 15 characters in name.