# Challenge 6: Monitor Azure File share and Azure File Sync

[< Previous Challenge](./Challenge-05-secure_private_endpoint.md) - **[Home](../README.md)**

## Pre-requisites

Deployment of environment described in Challenge 0 should be completed and validated. Azure Files deployed in Challenge 1 should be deployed and have some files.

## Introduction

In this challenge you will set up monitoring of Azure File share and Azure FileSync service.

## Description

1. Create new Log Analytics workspace.
1. Enable diagnostic settings for your Azure File share. Configure logs and metrics to flow to newly created Log Analytics workspace.
1. Create alert on Azure Files to monitor and alert when your Azure File share is throttled.
1. Create and run a Kusto querry in Log Analytics to find out how many files are stored on Azure File share.
1. Observe metrics for Azure File Sync service in Azure Monitor

## Success Criteria

At the end of this challenge you should have Azure File share monitored and set alerts when Azure File share gets throttled.

## Learning Resources

- [Monitoring Azure Files](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-monitoring?tabs=azure-portal)
- [Monitor Azure File Sync](https://docs.microsoft.com/en-us/azure/storage/file-sync/file-sync-monitoring)
- [Log Analytics tutorial](https://docs.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-tutorial)

## Tips

- Monitoring 