# deploy-terraform-in-azure
Deploying Infrastructure to Azure


## Overview

![terraform](https://www.datocms-assets.com/2885/1508512931-blog-terraform-list.svg)
![azure](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20180821105618/Microsoft_Azure_Logo.png)


The object I set out to do was to use terraform to easily deploy infrastructure into Azure using Azure CLI

***

#### Installing Terraform on Windows

Windows Version 1903 (OS Build 18342.8)

Download terraform from Terraform website for the required platform. In my case Windows. Create directory C:\Windows\Program Files\terraform copy the terraform.exe into the folder


### Create Terraform Files

Creating main files (.tf extension) used by terraform for this particular demo include main, providers, and variables.

Each contains the required code in order for the infrastructure to deploy.

#### Define and authenticate Azure details

First off the providers.tf, this is used to define the subscription, client_id, client_secret, and tenant_id

```
provider "azurerm" {
subscription_id = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
client_id = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
client_secret = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
tenant_id = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
}
```
subscription_id = subscription_id
client_id = 
client_secret = 
tenant_id = 
#### 
