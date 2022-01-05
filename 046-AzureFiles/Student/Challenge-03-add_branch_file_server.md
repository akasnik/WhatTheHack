# Challenge 3: Add Branch File Server as a new server endpoint

[< Previous Challenge](./Challenge-02-server_endpoints.md) - **[Home](../README.md)** - [Next Challenge >](./Challenge-04-add_data_protection.md)

## Pre-requisites

Deployment of environment described in [Challenge 0](./Challenge-00-lab_setup.md) should be completed and validated, Azure File share and Storage Sync Service should be deployed and configured with Cloud Endpoint and Server Endpoint. HQ File server and Azure File share should be synced.

## Introduction

In this challenge you will set up a Branch server to cache files for users in your Branch office location. Branch server will be synced to the same Azure File share as HQ server, therefore users in the branch office should have access to same files as users in HQ.

## Description

1. Create a folder to store file share data on your Branch server F: volume (vm-branch1-fs-1).
1. Deploy Azure File Sync Agent on your branch server.
1. Register Branch File Server with Storage Sync Service.
1. Add Branch File Server with Folder you created as a new Server endpoint to existing Sync Group. Enable Cloud Tiering for this Server Endpoint, you can leave default cloud tiering settings.
1. Verify that you are able to list and access files on your Branch Server in Folder you created. Note that it may take couple of minutes for initial sync to complete.
1. Modify file(s) on Branch server file share and verify replications

## Success Criteria

At the end of this challenge you should have Azure File share and Branch File server synchronized. Changes on any Server endpoint should be syncronized to other File server.

## Learning Resources

- [Install the Azure File Sync agent](https://docs.microsoft.com/azure/storage/file-sync/file-sync-deployment-guide#install-the-azure-file-sync-agent)
- [Register Windows Server with Storage Sync Service](https://docs.microsoft.com/azure/storage/file-sync/file-sync-deployment-guide#register-windows-server-with-storage-sync-service)
- [Cloud tiering overview](https://docs.microsoft.com/azure/storage/file-sync/file-sync-cloud-tiering-overview)

## Tips

- Use Azure Bastion to connect to the VM when deploying File Sync agent