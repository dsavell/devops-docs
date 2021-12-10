# Style Guide

## Rules

### Naming Conventions

Note: These conventions refer to Terraform names themselves, **NOT** cloud resources**.**

1. Use `_` (underscores) instead of `-` (dash) in all Resource/Data Source/Variable/Output/Local/Module names.

* Good: `resource "example_resource" "example_name" {}`
* Bad: `resource "example_resource" "example-name" {}`

2\. **MUST** be lowercase.

* Good: `resource "example_resource" "example_name" {}`
* Bad: `resource "example_resource" "EXAMPLE_NAME" {}`

3\. Always use singular nouns.

* Good: `resource "example_resource" "example" {}`
* Bad: `resource "example_resource" "examples" {}`

### Indentation

1. **MUST** be 2 spaces for each nesting level.

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

### Code Style

1. Style **MUST** follow the conventions set by Terraform & `terraform fmt` CLI command stated in the below documentation.

**NOTE:** Running `terraform fmt` will enforce the below automatically.

{% embed url="https://www.terraform.io/docs/language/syntax/style.html" %}
