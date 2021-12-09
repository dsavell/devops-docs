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

* Good: `` resource "example_resource" "example" {}` ``
* Bad: `resource "example_resource" "examples" {}`

### Indentation

1. **MUST** be 2 spaces, aswell as for each nested code block.

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
