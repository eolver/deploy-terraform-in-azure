# deploy-terraform-in-azure
Deploying Infrastructure to Azure


## Overview

![terraform](https://www.datocms-assets.com/2885/1508512931-blog-terraform-list.svg)
![azure](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20180821105618/Microsoft_Azure_Logo.png)


The object I set out to do was to use terraform to easily deploy infrastructure into Azure using Azure CLI. In this case I will be deploying a loan balancer with 2 virtual machines. This is more to demonstrate how you can deploy infrastrucutre only using terraform in azure.

***

#### Installing Terraform on Windows

Windows Version 1903 (OS Build 18342.8)

Download terraform from Terraform website for the required platform. In my case Windows. Create directory C:\Windows\Program Files\terraform copy the terraform.exe into the folder


### Create Terraform Files

Creating main files (.tf extension) used by terraform for this particular demo include main, providers, and variables.

Each contains the required code in order for the infrastructure to deploy.

#### Define and authenticate Azure details

##### providers.tf

Azure requires that an application is added to Azure Active Directory to generate the client_id, client_secret, and tenant_id needed by Terraform (subscription_id can be recovered from your Azure account details). Please go here for full instructions on how to create this to populate your provider.tf file.

this is used to define the subscription, client_id, client_secret, and tenant_id needed by Terraform. Azure requires that you create an application (in Azure Active Directory service) to generate teh client_id and client_secret)

```
provider "azurerm" {
subscription_id = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
client_id = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
client_secret = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
tenant_id = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
}
```
subscription_id = subscription_id
client_id = Application ID (Under App Registrations)
client_secret = Key (Generated in Application Settings)
tenant_id = Directory_ID (Azure AD Properties) 
#### 

##### main.tf

this is used to define the actual infrastructure to deploy.

##### variables.tf

This contains the input variables an Administrator/Developer/Contributer can deifne when deploying the template.
