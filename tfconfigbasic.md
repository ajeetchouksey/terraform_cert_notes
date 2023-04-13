# Terraform Configuration - Basic Concepts
## Terraform Object types

In Terraform, there are several object types that are **used to represent various kinds of resources, variables, outputs, and other configurations**. Following are some examples of each:

### Resource:
 A resource is the most commonly used object type in Terraform. **It represents a piece of infrastructure that needs to be created, updated, or deleted**. Below is an example of creating an AWS EC2 instance resource:

![Resources Object Type](/images/tf_config_concept1.jpg "Resources Object Type").

```
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "example-instance"
  }
}

}

```