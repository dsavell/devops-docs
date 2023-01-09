# Monorepo Code Structure

### Overview

```
└── terraform-azurerm-modules
    ├── azurerm_resource_group
    │   ├── data-sources.tf
    │   ├── examples
    │   │   └── minimal
    │   │       ├── main.tf
    │   │       └── providers.tf
    │   ├── locals.tf
    │   ├── outputs.tf
    │   ├── README.md
    │   ├── r-management-lock.tf
    │   ├── r-resource-group.tf
    │   ├── test
    │   │   ├── azurerm_resource_group_minimal_test.go
    │   │   ├── go.mod
    │   │   └── go.sum
    │   ├── variables.tf
    │   └── versions.tf
    ├── azurerm_subnet
    │   ├── data-sources.tf
    │   ├── examples
    │   │   └── minimal
    │   │       ├── main.tf
    │   │       └── providers.tf
    │   ├── locals.tf
    │   ├── outputs.tf
    │   ├── README.md
    │   ├── r-subnet.tf
    │   ├── test
    │   │   ├── azurerm_subnet_minimal_test.go
    │   │   ├── go.mod
    │   │   └── go.sum
    │   ├── variables.tf
    │   └── versions.tf
    ├── azurerm_virtual_network
    │   ├── data-sources.tf
    │   ├── examples
    │   │   └── minimal
    │   │       ├── main.tf
    │   │       └── providers.tf
    │   ├── locals.tf
    │   ├── outputs.tf
    │   ├── README.md
    │   ├── r-virtual-network.tf
    │   ├── test
    │   │   ├── azurerm_virtual_network_minimal_test.go
    │   │   ├── go.mod
    │   │   └── go.sum
    │   ├── variables.tf
    │   └── versions.tf
    ├── .gitattributes
    ├── .github
    │   ├── dependabot.yml
    │   └── workflows
    │       ├── azurerm_resource_group_ci.yaml
    │       ├── azurerm_subnet_ci.yaml
    │       ├── azurerm_virtual_network_ci.yaml
    │       └── composite
    │           ├── integration
    │           │   └── action.yml
    │           ├── lint
    │           │   └── action.yml
    │           ├── security
    │           │   └── action.yml
    │           └── validate
    │               └── action.yml
    ├── .gitignore
    ├── .pre-commit-config.yaml
    ├── README.md
    └── .terraform-version
```
