# Challenge 4: Enable Data Protection - Snapshot or Azure Backup - Coach's Guide

[< Previous Challenge](./03-add_branch_file_server.md) - **[Home](./README.md)** - [Next Challenge >](./05-secure_private_endpoint.md)

## Notes and Guidance


## Solution Guide
Create snapshots, and configure Azure Backup.

1. Snapshot Management
    - Refer https://docs.microsoft.com/en-us/azure/storage/files/storage-snapshots-files
    - Go to Azure File share. Under operations blade, you can see all the snapshots for this file share. 
    - Take a manual snapshot by going to Azure File share > Snapshots. Click Add Snapshot, provide a comment and select Ok.
    - Corrupt a file by making some changes to a file under HQ File share from the file server like deleting a line or overwriting the content with something. Check whether the file have sync'd to cloud.
    - To restore the corrupt file, go to Azure file share > Snapshots > Select the last snapshot created. You can access all the folder and files from the snapshot and restore just the corrupted file to its original location. Select the file to restore, click Restore. Select overwrite original file.
    - Check if the file restored was successful and verify the original content.

2. Enable backup for file share using Azure Backup
    - Follow steps here below to create a Recovery Services Vault and configure backup.
    - Steps: https://docs.microsoft.com/en-us/azure/backup/backup-afs?toc=/azure/storage/files/toc.json

3. Run an on-demand backup job (Backup Now)
    - Follow https://docs.microsoft.com/en-us/azure/backup/backup-afs?toc=/azure/storage/files/toc.json#run-an-on-demand-backup-job

4. Once backup job is complete, delete few files/folders from HQ File Server.

5. Restore files to original location using Azure Backup - Restore operation.
    - You can do a full share recovery to original location or another location and also perform item-level recovery.
    - Follow https://docs.microsoft.com/en-us/azure/backup/restore-afs?toc=/azure/storage/files/toc.json