<img width="100" alt="terraform-logo" src="https://user-images.githubusercontent.com/96013623/233460612-6b8966eb-f8b7-45bb-b9e5-ad6a0d0388a6.png">

### Terraform-Documentation

**Benefits of Terraform**
Let’s look at why so many people appreciate Terraform

**Declarative nature.** A declarative tool allows users to specify the end state and the IaC tools will automatically carry out the necessary steps to achieve the user configuration. It is in contrast to other imperative IaC tools where users need to define the exact steps required to achieve the desired state.

**Platform agnostics.** Most IaC tools like AWS CloudFormation and Azure Resource templates are platform specific. Yet, Terraform allows users to use a single tool to manage infrastructure across platforms with applications using many tools, platforms, and multi-cloud architectures.

**Reusable configurations.** Terraform encourages the creation of reusable configurations where users can use the same configuration to provision multiple environments. Additionally Terraform allows creating reusable components within the configuration files with modules.

**Managed state.** With state files keeping track of all the changes in the environment, all modifications are recorded and any unnecessary changes will not occur unless explicitly specified by the user. It can be further automated to detect any config drifts and automatically fix the drift to ensure the desired state is met at all times.

**Easy rollsbacks.** As all configurations are version controlled and the state is managed, users can easily and safely roll back most infrastructure configurations without complicated reconfigurations.

**Integration to CI/CD.** While IaC can be integrated into any pipeline, Terraform provides a simple three-step workflow that can be easily integrated into any CI/CD pipeline. It helps to completely automate the infrastructure management.

https://www.bmc.com/blogs/terraform/

### What Are the Providers in Terraform?

A provider in Terraform is a plugin that enables interaction with an API. This includes Cloud providers and Software-as-a-service providers. The providers are specified in the Terraform configuration code. They tell Terraform which services it needs to interact with.

![image](https://user-images.githubusercontent.com/96013623/233902274-d8c140ff-57a3-44c5-a91a-c4834d8ecef8.png)

https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs

**Authentication to Azure**

https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs#authenticating-to-azure

**Feature block**
https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/guides/features-block

Managed Identity Doc: https://learn.microsoft.com/en-in/azure/active-directory/managed-identities-azure-resources/overview

If the provider version is old and you have mentioned a new version so you might have to use:

terraform init -upgrade

Attributes:

In terraform the attribute of resource can be exported and as you need is:

azurerm_subnet ---> resource type
name --> name of subnet
id --> (the attribute it will fetch automatically)

https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_interface

 ip_configuration {
    name                          = "internal"
    subnet_id                     = azurerm_subnet.example.id
    private_ip_address_allocation = "Dynamic"
  }
}

as in example above subnet id
