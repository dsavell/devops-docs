# Style Guide

### Rules

#### Naming

1. Use \_ (underscores) instead of - (dash) in all Resource/Data Source/Input Variable/Output Values/Local Values/Module names. Also known as \[Snake Case]\([https://en.wikipedia.org/wiki/Snake\_case](https://en.wikipedia.org/wiki/Snake\_case))

Good Example:

```
resource "example_resource" "example_name" {
  ...
}

data "example_data_source" "example_name" {
  ...
}

variable "example_variable" {
  ...
}

output "example_output" {
  ...
}

module "example_module" {
  ...
}
```

Bad Example:

```
resource "example_resource" "example-name" {
  ...
}

data "example_data_source" "example-name" {
  ...
}

variable "example-variable" {
  ...
}

output "example-output" {
  ...
}

module "example-module" {
  ...
}
```

2\. Names **MUST** be lowercase.

Good Example:

```
resource "example_resource" "example_name" {
  ...
}

data "example_data_source" "example_name" {
  ...
}

variable "example_variable" {
  ...
}

output "example_output" {
  ...
}

module "example_module" {
  ...
}
```

Bad Example:

```
resource "example_resource" "EXAMPLE_NAME" {
  ...
}

data "example_data_source" "EXAMPLE_NAME" {
  ...
}

variable "EXAMPLE_VARIABLE" {
  ...
}

output "EXAMPLE_OUTPUT" {
  ...
}

module "EXAMPLE_MODULE" {
  ...
}
```

#### Indentation

Iindentations **MUST** be 2 spaces, aswell as for each nested code block.

Never use tabs or mix tabs and spaces.

Good Example:

```
resource "example_resource" "example_name" {
  resource_name = "example_name"
  
  example_attribute {
    example_attribute {
    }
  }

}
```

Bad Example

```
resource "example_resource" "example_name" {
    resource_name = "example_name"
    
    example_attribute {
        example_attribute {
        }
    }
}
```



