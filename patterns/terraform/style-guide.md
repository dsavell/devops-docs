# Style Guide

## Rules

### Naming Conventions

Note: These conventions refer to Terraform names themselves, **NOT cloud resources.**

1. Use \_ (underscores) instead of - (dash) in all Resource/Data Source/Variable/Output/Local/Module names.

* Good: `resource "azurerm_resource_group" "example_name" {}`
* Bad: `resource "azurerm_resource_group" "example-name" {}`

2\. **MUST** be lowercase.

* Good: `resource "azurerm_resource_group" "example_name" {}`
* Bad: `resource "azurerm_resource_group" "EXAMPLE_NAME" {}`

3\. Always use singular nouns.

* Good: `resource "azurerm_resource_group" "firewall" {}`
* Bad: `resource "azurerm_resource_group" "firewalls" {}`

### Indentation

1. **pdatedMUST** be 2 spaces, aswell as for each nested code block.

Good:

```
resource "example_resource" "example_name" {
  resource_name = "example_name"
  
  example_attribute {
    example_attribute {
    }
  }

}
```

Bad:

```
resource "example_resource" "example_name" {
    resource_name = "example_name"
    
    example_attribute {
        example_attribute {
        }
    }
}
```
