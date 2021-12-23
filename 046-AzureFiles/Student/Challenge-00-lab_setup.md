# Challenge 0: Environment Setup

**[Home](../README.md)** - [Next Challenge >](./Challenge-01-set_files_and_filesync.md)

## Description

Environment that will be beployed in this challenge is required before starting with next challenges. It will be deployed in series of VMs in Azure with configurations that include Active Directory Domain and File Server(s) so it takes a while to deploy and configure (estimate 30 min).

Environment is deployed by executing deployment of provided Bicep templates. Configurations are done by using provided PowerShell DSC configurations. Templates will deploy the following components across 3 different Azure regions:
- On-prem (HQ - North Europe and Branch Site - UK South):
    - HQ Domain Controller - contoso.com (vm-hq-dc)
    - HQ File Server (vm-hq-fs-1)
    - Client Machine (vm-hq-client-1)
    - Branch File Server (vm-branch1-fs-1)
- Azure (Hub - West Europe)
    - Virtual Network (vnet-azhub)
    - Azure App VM (vm-az-app-1)
- Azure Bastion to access environment
- VNet peering is used for simplified connectivity between HQ and Branch, HQ and Azure Hub.

![Architecture diagram illustrating an environment for Azure Files lab](../images/1-architecture-diagram.png)

## Deploy lab template using templates

Steps to deploy Azure Files lab environment:

1. Fork this GitHub repo and clone to your computer with latest Azure Powershell module or Azure CLI.
2. Login to your Azure subscription using PowerShell or Azure CLI.
    - AZ CLI: az login
    - PowerShell: Connect-AzAccount
        - az account set --subscription "Subscription Name"
3. Create a resource group in Azure where lab environment will be deployed.
    - AZ CLI: az group create -n 'rg-lab-afs' -l 'westeurope'
    - PowerShell: New-AzResourceGroup -Name 'rg-lab-afs' -Location 'westeurope'
4. (Optional) Modify parameter values within "./bicep/azfiles-lab.parameters.json" file if required.
5. Initiate template deployment.
    - Switch to the .\bicep\ folder. 
    - AZ CLI:  az deployment group create -g 'rg-lab-afs' -f .\azfiles-lab.json --parameters .\azfiles-lab.parameters.json
    - Powershell: New-AzResourceGroupDeployment -Name AzFilesLab -ResourceGroupName 'rg-lab-afs' -TemplateFile .\azfiles-lab.json -TemplateParameterFile .\azfiles-lab.parameters.json
6. Type password to be used for all accounts (including domain admin) in your lab environment. Be sure to remember that password as you will need it to log into the lab environment.
7. Wait for deployment to finish, it should take around 30 minutes for deployment to finish.

### Validate Lab
Steps to check connectivity and validate whether DSC has completed the required configurations for the base lab to start with various challenges (exercises) below.

1. Connect to all VMs using Bastion.  
*Note: if you haven't changed deployment parameters, default administrator username will be 'azadmin'; use the password that you entered as parameter at the start of deployment; default domain name is 'contoso.com')*
2. Validate Domain Controller, check Computers OU objects - make sure all machines are domain joined.
3. Connect to HQ File Server, validate F:\Share1 exist with some dummy folder and files.
4. Connect to HQ-Client-1, open elevated command prompt or powershell and run below command to map the file share to a local M: drive on the VM.
    - net use M: \\vm-hq-fs-1\Share1 /persistent:Yes
5. Edge browser is deployed on servers for internet access/file downloads.