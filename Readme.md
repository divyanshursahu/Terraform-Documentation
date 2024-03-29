<img width="300" alt="terraform-logo" src="https://upload.wikimedia.org/wikipedia/commons/0/04/Terraform_Logo.svg"> 

## What is Terraform ?

Terraform is an Infrastructure as Code (IaC) software tool offered by HashiCorp, that lets you provision and manage your infrastructure in the cloud (AWS, Azure, GCP, etc) and on-prem resources. It lets you define both Cloud and on-prem resources in human-readable configuration files that you can version, reuse, and share.

## What is IAC (Infrastructure as a Code)

Infrastructure as code (IaC) is the process that allows you to manage infrastructure with configuration files rather than through a graphical user interface. IaaC allows you to build, change, and manage your infrastructure in a safe, consistent, and repeatable way by defining resource configurations that you can version, reuse, and share.

## Why Terraform

**1. Manage any infrastructure**
   - You can provision infra for any cloud provider and platform available in [Terraform Registry](https://registry.terraform.io/?product_intent=terraform)

**2. Track your infrastructure**
   - Terraform generates a plan and prompts you for your approval before modifying your infrastructure.
   - It also keeps track of your real infrastructure in a state file, which acts as a source of truth for your environment.
   
**3. Automate changes**
   - Terraform configuration files are declarative, meaning that they describe the end state of your infrastructure.
   - Terraform builds a resource graph to determine resource dependencies and creates or modifies non-dependent resources in parallel. 
 
**4. Standardize configurations**
   - Terraform supports reusable configuration components called modules that define configurable collections of infrastructure, saving time and encouraging best practices.
   - You can use publicly available modules from the Terraform Registry, or write your own.
     
**5. Collaborate**
   - Since your configuration is written in a file, you can commit it to a Version Control System (VCS) and use Terraform Cloud to efficiently manage Terraform workflows across teams.

## How does Terraform work

Terraform creates and manages resources on cloud platforms and other services through their application programming interfaces (APIs). Providers enable Terraform to work with virtually any platform or service with an accessible API.

![image](https://github.com/divyanshursahu/Terraform-Documentation/assets/96013623/ff53ea1d-3587-42e1-ae04-615ce5242181)

The core Terraform workflow consists of three stages:

**Write:** You define resources, which may be across multiple cloud providers and services. 

**Plan:** Terraform creates an execution plan describing the infrastructure it will create, update, or destroy based on the existing infrastructure and your configuration.

**Apply:** On approval, Terraform performs the proposed operations in the correct order, respecting any resource dependencies.

![image](https://github.com/divyanshursahu/Terraform-Documentation/assets/96013623/534afbe8-df89-490d-ba62-35ed01baf8c4)

     
## Terraform Commands

### Get help

- ``` terraform -help  ``` &mdash; Get a list of available commands for execution with descriptions. Can be used with any other subcommand to get more information.

-  ```terraform fmt -help```  &mdash; Display help options for the ```fmt``` command

###  Show Your Terraform Version

- ```terraform version``` &mdash; Show the current version of your  Terraform and notifies you if there is a newer version available for download.

### Format Your Terraform Code

This command can be used to format your configuration files and ensures it is formatted using HCL standards.

- ```terraform fmt``` &mdash; This formats your terraform configuration files using the HCL Language standard.
  
- ```terraform fmt --recursive``` &mdash; Also format files in subdirectories
  
- ```terraform fmt --diff``` &mdash; displays difference between orignal configuration files and formatting changes.
  
- ```terraform fmt --check``` &mdash; the check flag can be used to ensure the configuration files are formatted correctly, if not the exit status will be non-zero. If files are formatted correctly, the exit status will be zero.

### Initialize Your Directory 

- ```terraform init``` &mdash; it is used to initialize the working directory for use with terraform. It download the required provider packages and also perform backend installation, Child module Installation, and plugin installation.

- ```terraform init -get-plugins=false``` &mdash; Initialize the working directory, do not download plugins.

- ```terraform init -lock=false``` &mdash; Initialize the working directory, don’t hold a state lock during backend migration.

- ```terraform init -input=false``` &mdash; Initialize the working directory, and disable interactive prompts.

- ```terraform init -migrate-state``` &mdash; Reconfigure a backend, and attempt to migrate any existing state.

- ```terraform init -verify-plugins=false``` &mdash; Initialize the working directory, do not verify plugins for Hashicorp signature

### Validate your Terraform Code

- ```terraform validate``` &mdash; Validate the configuration files in your directory and does not access any remote state or services. terraform init should be run before this command.

- ```terraform validate -json``` &mdash; To see easier the number of errors and warnings that you have.

### Plan your Infrastructure

- ```terraform plan``` &mdash; Plan will generate execution plan, showing you what actions will be taken without acutally performing the planned actions.

- ```terraform plan -out=<path>``` &mdash; Save the plan file to a given path. Can then be passed to the terraform apply command.

- ```terraform plan -destroy``` &mdash; Create a plan to destroy all objects rather than the usual actions.

### Deploy your Infrastructure

- ```terraform apply``` &mdash; Create or update infrastructure depending on the configuration files. By default, a plan will be generated first and will need to be approved before it is applied.

- ```terraform apply -auto-approve``` &mdash; Apply changes without having to interactively type ‘yes’ to the plan. Useful in automation CI/CD pipelines.

- ```terraform apply <planfilename>``` &mdash; Provide the file generated using the terraform plan -out command. If provided, Terraform will take the actions in the plan without any confirmation prompts.

- ```terraform apply -lock=false``` &mdash; Do not hold a state lock during the Terraform apply operation. Use with caution if other engineers might run concurrent commands against the same workspace.

- ```terraform apply -parallelism=<n>``` &mdash; Specify the number of operations run in parallel.

- ```terraform apply -var="environment=dev"``` &mdash; Pass in a variable value.

- ```terraform apply -var-file="varfile.tfvars"``` &mdash; Pass in variables contained in a file.

- ```terraform apply -target=”module.appgw.0"``` &mdash; Apply changes only to the targeted resource.

### Destroy your Infrastructure

- ```terraform destroy``` &mdash; Destroy the infrastructure managed by Terraform.

- ```terraform destroy -target=”module.appgw.0"``` &mdash; Destroy only the targeted resource.

- ```terraform destroy --auto-approve``` &mdash; Destroy the infrastructure without having to interactively type ‘yes’ to the plan. Useful in automation CI/CD pipelines.

- ```terraform destroy -target="module.appgw.resource[\"key\"]"``` &mdash; Destroy an instance of a resource created with for_each.


### ‘Taint’ or ‘Untaint’ Your Resources

Use the taint command to mark a resource as not fully functional. It will be deleted and re-created.

```terraform taint vm1.name``` &mdash; Taint a specified resource instance.

```terraform untaint vm1.name``` &mdash; Untaint the already tainted resource instance.

### Refresh the State File

```terraform refresh``` &mdash; Modify the state file with updated metadata containing information on the resources being managed in Terraform. Will not modify your infrastructure.

### View Your State File

```terraform show``` &mdash; Show the state file in a human-readable format.

```terraform show <path to statefile>``` &mdash; If you want to read a specific state file, you can provide the path to it. If no path is provided, the current state file is shown.

### Manipulate Your State File

```terraform state``` &mdash; One of the following subcommands must be used with this command in order to manipulate the state file.

```terraform state list``` &mdash; Lists out all the resources that are tracked in the current state file.

```terraform state mv``` &mdash; Move an item in the state, for example, this is useful when you need to tell Terraform that an item has been renamed, e.g. terraform state mv vm1.oldname vm1.newname

```terraform state pull > state.tfstate``` &mdash; Get the current state and outputs it to a local file.

```terraform state push``` &mdash; Update remote state from the local state file.

```terraform state replace-provider hashicorp/azurerm customproviderregistry/azurerm``` &mdash; Replace a provider, useful when switching to using a custom provider registry.

```terraform state rm``` &mdash; Remove the specified instance from the state file. Useful when a resource has been manually deleted outside of Terraform.

```terraform state show <resourcename>``` &mdash; Show the specified resource in the state file.

### Import Existing Infrastructure into Your Terraform State

```terraform import vm1.name -i id123``` &mdash; Import a VM with id123 into the configuration defined in the configuration files under vm1.name.

### lifecycle Meta-Argument

The lifecycle block provides several meta-arguments to manage how Terraform creates, updates, checks and deletes resources. 

lifecycle is a nested block that can appear within a resource block. The lifecycle block and its contents are meta-arguments, available for all resource blocks regardless of type.

Reference: https://dev.to/pwd9000/terraform-understanding-the-lifecycle-block-4f6e
 

The arguments available within a lifecycle block are create_before_destroy, prevent_destroy, ignore_changes, and replace_triggered_by
