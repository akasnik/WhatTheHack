# What The Hack - Azure Files and FileSync

## Introduction
The Azure Files and FileSync hack will take you through scenario of well known fictional company Contoso, that is in phase of moving their on-premise file servers to Azure Files. You will play key role in this endeavour as you'll be setting up Azure environment and necessary on-prem components required to implement hybrid environment with Azure Files and FileSync.

## Learning Objectives
In this hack you will be solving the common challenges that organizations face when moving their file servers to Azure. After completing, participants will be familiar with:

- Deploying Azure infrastructure required for Azure Files and FileSync
- Setting up synchronization between on-prem file server(s) and Azure Files
- Setting up file replication to branch site
- Protecting Azure Files data
- Securing access to Azure Files
- Integrating with on-prem Active Directory (AD DS) for seamless end-user access

![The Solution diagram is described in the text following this diagram.](images/1-architecture-diagram.png 'Solution diagram')

## Before you start
There is a lab environment that you need to deploy before starting with challenges. It will be deployed using series of VMs in Azure with configurations that include Active Directory Domain and File Server(s), so it takes a while to deploy and configure (estimate 30 min). Steps to deploy environment are provided in [**Challenge 0: Deploy lab using template**](Student/Challenge-00-lab_setup.md).

## Challenges
1. Challenge 0: **[Deploy lab using template](Student/Challenge-00-lab_setup.md)**
   - Deploy the base environment for the lab using Azure subscription. 
1. Challenge 1: **[Setup Azure Files and File Sync Service](Student/Challenge-01-set_files_and_filesync.md)**
   - Create Azure Files share, setup and configure Storage Sync Service.
1. Challenge 2: **[Configure Server endpoint and file synchronization](Student/Challenge-02-server_endpoints.md)**
   - Configure HQ File Server endpoint and setup cloud tiering.
1. Challenge 3: **[Add Branch File Server as a new server endpoint](Student/Challenge-03-add_branch_file_server.md)**
   - Configure Branch File Server to replicate/sync the files from Azure Files.
1. Challenge 4: **[Enable Data Protection - Snapshot or Azure Backup](Student/Challenge-04-add_data_protection.md)**
   - Review soft delete feature, manage snapshots, and configure Azure Backup.
1. Challenge 5: **[Secure Azure File Share with Private Endpoint](Student/Challenge-05-secure_private_endpoint.md)**
   - Configure storage firewall and enable private endpoint for secure access to Azure file share.
1. Challenge 6: **[Monitor Azure File share and Azure File Sync](Student/Challenge-06-monitor_file_share.md)**
   - Configure Azure File share and Azure File Sync monitoring
1. Challenge 7: **[Integrate Azure File share with Active Directory (AD DS)](Student/Challenge-07-ad_integration.md)**
   - Domain join Azure File storage account to AD DS for seamless user access to shares using existing ACLs

## Prerequisites
- Your own Azure subscription with Owner access
- Visual Studio Code
- Az PowerShell Module

## Repository Contents (Optional)
- `../Coach/Guides`
  - Coach's Guide and related files
- `../Student/Guides`
  - Student's Challenge Guide and related resources
- `../images`
  - Architecture diagrams and generic image files used


## Contributors
- Andrej Kasnik
- Jithin P P
