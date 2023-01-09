# Code Structure

## Overview

```
azurerm_resource_group/
├── data-sources.tf
├── examples
│   └── minimal
│       ├── main.tf
│       └── providers.tf
├── locals.tf
├── outputs.tf
├── README.md
├── r-management-lock.tf
├── r-resource-group.tf
├── test
│   ├── azurerm_resource_group_minimal_test.go
│   ├── go.mod
│   └── go.sum
├── variables.tf
└── versions.tf
```

### data-sources.tf

Contains all referenced data sources anything this module does not create itself. [https://developer.hashicorp.com/terraform/language/data-sources](https://developer.hashicorp.com/terraform/language/data-sources)

```
data "azurerm_client_config" "current" {}
```

### examples/

### locals.tf

Contains all local values and logic for generating values, this helps with the keep it DRY concept in your codebase. [https://developer.hashicorp.com/terraform/language/values/locals](https://developer.hashicorp.com/terraform/language/values/locals)

```
locals {
  required_tags = {
    "business-criticality" = var.business_criticality_tag
    "business-unit"        = var.business_unit_tag
    "data-classification"  = var.data_classification_tag
    "environment"          = var.environment_tag
    "operations-team"      = var.operations_team_tag
    "owners"               = var.owners_tag
    "project"              = var.project_tag
    "role"                 = var.role_tag
  }
}
```

### r-resource-group.tf / r-management-lock.tf

This file can be very opinionated usally `main.tf` but in my opinion I like to split out files based on the resource your deploying, this is just coming from an enterprise background here, but hear me out, when I have taken a look at codebases already established, most of the time I have come across 300/500+ lines of code within main.tf this makes it a bit of an eye sore for me that being said here is an example. Either way this is entirely how you want to read your codebase, it still gets rendered the same way.

```
# r-resource-group.tf
resource "azurecaf_name" "main" {
  resource_type = "azurerm_resource_group"
  suffixes      = [var.region_id, var.environment_id, var.role_id, var.identifier]
  separator     = "-"
}

resource "azurerm_resource_group" "main" {
  name     = azurecaf_name.rg_name.result
  location = var.location

  tags = merge(local.required_tags, var.extra_tags)
}

# r-management-lock.tf
resource "azurerm_management_lock" "ml" {
  count = var.enable_management_lock ? 1 : 0

  name       = "${azurecaf_name.rg_name.result}-lock"
  scope      = azurerm_resource_group.rg.id
  lock_level = var.lock_level
  notes      = "Resource Group '${azurecaf_name.rg_name.result}' is locked with '${var.lock_level}' level."
}
```

### outputs.tf

Contains all your module outputs this can help expose information for other Terraform configurations such as a resource ID. [https://developer.hashicorp.com/terraform/language/values/outputs](https://developer.hashicorp.com/terraform/language/values/outputs)

```
output "name" {
  description = "The name of the Resource Group."
  value       = azurerm_resource_group.rg.name
}

output "id" {
  description = "The ID of the Resource Group."
  value       = azurerm_resource_group.rg.id
}

output "location" {
  description = "The location (region) of the Resource Group."
  value       = azurerm_resource_group.rg.location
}
```

### README.md

Contiains the most important information for other users (some would say the most important)

1. Description of the module.
2. Usage of the module / links to examples.
3. Generated Terraform Docs
   1. Resources
   2. Providers
   3. Version constraints
   4. Modules
   5. Inputs
   6. Outputs

````
# azurerm_resource_group

Terraform module to create an Azure Resource Group with optional lock.

## Usage

```terraform
module "rg" {
  source =

  location =
}
```

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | ~> 1.1.0 |
| <a name="requirement_azurecaf"></a> [azurecaf](#requirement\_azurecaf) | ~> 1.2.0 |
| <a name="requirement_azurerm"></a> [azurerm](#requirement\_azurerm) | ~> 2.90.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_azurecaf"></a> [azurecaf](#provider\_azurecaf) | ~> 1.2.0 |
| <a name="provider_azurerm"></a> [azurerm](#provider\_azurerm) | ~> 2.90.0 |

## Modules

No modules.
````

### test/

### variables.tf

Contains all your input modules, this allows modifications to modules without altering the code. [https://developer.hashicorp.com/terraform/language/values/variables](https://developer.hashicorp.com/terraform/language/values/variables)

```
variable "location" {
  description = "The Azure Region where the Resource Group should exist. Changing this forces a new resource to be created."
  type        = string
}

variable "environment_tag" {
  description = "Deployment environment of the resource, application, role, workload, or service."
  type        = string
}

variable "lock_level" {
  description = "Specifies the Level to be used for this management Lock. Possible values are CanNotDelete and ReadOnly. Changing this forces a new resource to be created."
  type        = string
  default     = null
}
```

### versions.tf

versions.tf contains your acceptable versions for things such as providers & terraform version requirements. [https://developer.hashicorp.com/terraform/language/expressions/version-constraints](https://developer.hashicorp.com/terraform/language/expressions/version-constraints)

```
terraform {
  required_version = "~> 1.3.0"
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "~> 3.30.0"
    }
  }
}
```

