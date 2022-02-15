# Challenge 5: Secure Azure File Share with Private Endpoint

[< Previous Challenge](./Challenge-04-add_data_protection.md) - **[Home](../README.md)** - [Next Challenge >](./Challenge-06-monitor_file_share.md)

## Pre-requisites

- Deployment of environment described in [Challenge 0](./Challenge-00-lab_setup.md) should be completed and validated.
- Azure Files deployed in Challenge 1 should be deployed and have some files.

## Introduction

Using Private Endpoints you enable connectivity to Azure File share and Azure FileSync service from within Azure Virtual Network. Using Private Endpoints you can block Public Endpoints to Azure File share and FileSync service and provide connectivity from on-prem via VPN or ExpressRoute connection.

## Description

1. Create Private Endpoint for your Azure File share, make sure that Private Endpoint is created in same VNet that was deployed in Challenge 0, or in different VNet that has VNet Peering enabled with VNet deployed in Challenge 0.
1. Restrict Public Endpoint access on Storage Account hosting your Azure File share.
1. Create Private Endpoint for Storage Sync Services in same VNet as Private Endpoint for Azure File share.
1. Restrict public access to Storage Sync Services. 

## Success Criteria

At the end of this challenge your Azure File share and Storage Sync Services should be only available through Private Endpoints and have Public access blocked.

## Learning Resources

- [Azure Files networking considerations](https://docs.microsoft.com/azure/storage/files/storage-files-networking-overview)
- [Configuring Azure Files network endpoints](https://docs.microsoft.com/azure/storage/files/storage-files-networking-endpoints)
- [Storage account firewall settings](https://docs.microsoft.com/azure/storage/files/storage-files-networking-overview#storage-account-firewall-settings)
- [Azure File Sync networking considerations](https://docs.microsoft.com/azure/storage/file-sync/file-sync-networking-overview)
- [Configuring Azure File Sync network endpoints](https://docs.microsoft.com/azure/storage/file-sync/file-sync-networking-endpoints)

## Tip

- Enabling Private Endpoint for Azure File share is important consideration when you plan to mount Azure File share from on-prem servers or clients as SMB port 445 is often blocked by service providers, which makes it challenging to connect to Azure File share public endpoint over internet.
- To restrict public access to Storage Sync Services you will need to use PowerShell.