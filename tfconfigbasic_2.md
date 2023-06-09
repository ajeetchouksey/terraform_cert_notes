# Terraform Configuration - Basic Concepts
## Terraform Object types

In Terraform, there are several object types that are **used to represent various kinds of resources, variables, outputs, and other configurations**. Following are some examples of each:

### Resource:
 A resource is the most commonly used object type in Terraform. **It represents a piece of infrastructure that needs to be created, updated, or deleted**.

 #### AWS EC2
```
resource "aws_instance" "example" {
    ami           = "ami-0c55b159cbfafe1f0"
    instance_type = "t2.micro"
}
```
#### Azure 

```
resource "azurerm_resource_group" "example" {
    name     = "example"
    location = "West Europe"
    tags = {
        Name = "example-instance"
    }
}
```

### Variable: 
A variable is **used to pass data into a Terraform configuration**. It can be used to customize the behavior of a module or to provide input values for a resource. Below is an example of defining a variable:
```
variable "region" {
    type    = string
    default = "us-west-1"
}
```
### Output: 
An output is **used to expose data from a Terraform configuration**. It can be used to share information with other modules or to display values to the user. Here's an example of defining an output:
```
output "instance_public_ip" {
    value = aws_instance.example.public_ip
}
```
```
output "azurerm_resource_group" {
    value = azurerm_resource_group.example
}
```

### Data source: 
A data source is **used to retrieve information from an external system, such as AWS or Azure**. It can be used to reference an existing resource or to retrieve information that is needed to create a new resource. 

> Get AWS VPC id
```
data "aws_vpc" "example" {
  id = "vpc-12345678"
}
```
>  Get Resources from a Resource Group
```
data "azurerm_resources" "example" {
  resource_group_name = "example-resources"
}
```
### Provider: 
A provider is **used to configure and manage the lifecycle of an external service**, such as AWS or Azure. It is responsible for creating, updating, and deleting resources in that service.

```
provider "aws" {
  region = var.region
}
```

```
provider "azurerm" {
  features {
  }
}
```