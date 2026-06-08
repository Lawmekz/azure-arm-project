\# Azure ARM Template - VM Deployment



\## Overview

Deploys a Ubuntu 22.04 VM with full networking (VNet, NSG, NIC, Public IP)

using Azure Resource Manager (ARM) templates and Azure CLI.



\## Files

\- `azuredeploy.json` — Main ARM template

\- `azuredeploy.parameters.json` — Parameters file

\- `deployment-output.json` — Deployment output log



\## Deployment Commands



\### 1. Create Resource Group

```bash

az group create --name MyArmRG --location eastus2

```



\### 2. Validate

```bash

az deployment group validate --resource-group MyArmRG --template-file azuredeploy.json --parameters azuredeploy.parameters.json

```



\### 3. Deploy

```bash

az deployment group create --resource-group MyArmRG --template-file azuredeploy.json --parameters azuredeploy.parameters.json --name myArmDeployment

```



\### 4. Get Public IP

```bash

az deployment group show --resource-group MyArmRG --name myArmDeployment --query "properties.outputs.publicIPAddress.value" --output tsv

```



\## Resources Deployed

\- Network Security Group (SSH port 22, HTTP port 80)

\- Virtual Network (VNet) with subnet

\- Public IP Address (Standard SKU)

\- Network Interface Card (NIC)

\- Ubuntu 22.04 LTS Gen2 VM (Standard\_D2s\_v7)



\## Deployment Result

\- Public IP: 20.22.241.50

\- Status: Succeeded

