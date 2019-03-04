# deploy-terraform-in-azure
Deploying Infrastructure to Azure using Terraform (Infrastructure as Code)


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

this is used to define the subscription, client_id, client_secret, and tenant_id needed by Terraform. Azure requires that you create an application (in Azure Active Directory service) to generate teh client_id and client_secret) Once you create the App Registration you need to go to relevant subscription, Access Control (IAM) and define the role assignment (Contributer) to the App registered.

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

##### main.tf

this is used to define the actual infrastructure to deploy.

##### variables.tf

This contains the input variables an Administrator/Developer/Contributer can deifne when deploying the template.

### Run Terraform

Using powershell as administrator console, In my case VS Code. Browse to the required path where terraform has been installed. In this demo it has been installed C:\Program Files\Terraform\terraform.exe

```
cd\
cd '.\Program Files\terraform\'
terraform.exe init
```

This should validate terraform is running.

```
Initializing provider plugins...

The following providers do not have any version constraints in configuration,
so the latest version was installed.

To prevent automatic upgrades to new major versions that may contain breaking
changes, it is recommended to add version = "..." constraints to the
corresponding provider blocks in configuration, with the constraint strings
suggested below.

* provider.azurerm: version = "~> 1.22"

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```

#### Terraform Plan

Once you have succussfully got terraform running. you can now begin to execute the planning stages of the infrastructure you have set out to deploy by running terraform plan cmd. This will walk the the steps as if you were deploying and display a list of all infrastructure that will deployed.
