# What The Hack - Azure Files and FileSync

## Introduction
The Azure Files and FileSync hack will take you through scenario of well known fictional company Contoso, that is in phase of moving their File shares to Azure Files. You will play key role in this endavour as you'll be setting up Azure environment and reqiured on-prem components required to implement hybrid environment with Azure Files and FileSync.

## Learning Objectives
In this hack you will be solving the common challenges that organizations face when moving their file servers to Azure. After completing participants will be familiar with:

- Deploying Azure infrastructure required for Azure Files and FileSync
- Seting up synchronization between on-prem file server and Azure Files
- Protecting Azure Files data
- Securing access to Azure Files

## Before you start
There is environment that you need to deploy before starting with challenges. It will be deployed in series of VMs in Azure with configurations that include Active Directory Domain and File Server(s) so it takes a while to deploy and configure (estimate 30 min). Steps to deploy environment are provided in [**Challenge 0**](Student/Challenge-00-lab_setup.md).

## Challenges
1. Challenge 0: **[Deploy lab using template](Student/Challenge-00-lab_setup.md)**
   - Deploy the base environment for the lab using Azure subscription. 
1. Challenge 1: **[Setup Azure Files and File Sync Service](Student/Challenge-01-set_files_and_filesync.md)**
   - Create Azure Files share, setup and config Storage Sync Service.
1. Challenge 2: **[Configure Server endpoint and Cloud tiering](Student/Challenge-02-server_endpoints_tiering.md)**
   - Config HQ File Server endpoint and setup cloud tiering.
1. Challenge 3: **[Add Branch File Server as a new server endpoint](Student/Challenge-03-add_branch_file_server.md)**
   - Config Branch File Server to replicate/sync the files from Azure Files.
1. Challenge 4: **[Enable Data Protection - Snapshot or Azure Backup](Student/Challenge-04-add_data_protection.md)**
   - Review soft delete feature, manage snapshots, and configure Azure Backup.
1. Challenge 5: **[Secure Azure File Share with Private Endpoint](Student/Challenge-05-secure_private_endpoint.md)**
   - Configure storage firewall and enable private endpoint for secure access to Azure file share.

## Prerequisites
- Your own Azure subscription with Owner access
- Visual Studio Code
- Az PowerShell Module

## Repository Contents (Optional)
- `../Coach/Guides`
  - Coach's Guide and related files
- `../SteamShovel`
  - Image files and code for steam shovel microservice
- `../images`
  - Generic image files needed
- `../Student/Guides`
  - Student's Challenge Guide

## Contributors
- Andrej Kasnik
- Jithin P P
