---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Introduction

### What is IAC (Infrastructure as a Code)

Infrastructure as code (IaC) is the process that allows you to manage infrastructure with configuration files rather than through a graphical user interface. IaaC allows you to build, change, and manage your infrastructure in a safe, consistent, and repeatable way by defining resource configurations that you can version, reuse, and share.

### Why Terraform

**1. Manage any infrastructure**

* You can provision infra for any cloud provider and platform available in [Terraform Registry](https://registry.terraform.io/?product\_intent=terraform).

**2. Track your infrastructure**

* Terraform generates a plan and prompts you for your approval before modifying your infrastructure.
* It also keeps track of your real infrastructure in a state file, which acts as a source of truth for your environment.

**3. Automate changes**

* Terraform configuration files are declarative, meaning that they describe the end state of your infrastructure.
* Terraform builds a resource graph to determine resource dependencies and creates or modifies non-dependent resources in parallel.

**4. Standardize configurations**

* Terraform supports reusable configuration components called modules that define configurable collections of infrastructure, saving time and encouraging best practices.
* You can use publicly available modules from the Terraform Registry, or write your own.

**5. Collaborate**

* Since your configuration is written in a file, you can commit it to a Version Control System (VCS) and use Terraform Cloud to efficiently manage Terraform workflows across teams.

### How does Terraform work

Terraform creates and manages resources on cloud platforms and other services through their application programming interfaces (APIs). Providers enable Terraform to work with virtually any platform or service with an accessible API.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

**The core Terraform workflow consists of three stages:**

1. **Write:** You define resources, which may be across multiple cloud providers and services.
2. **Plan:** Terraform creates an execution plan describing the infrastructure it will create, update, or destroy based on the existing infrastructure and your configuration.
3. **Apply:** On approval, terraform performs the proposed operations in the correct order, respecting any resource dependencies.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>
