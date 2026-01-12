# Terraform in Action

**Date:** 12 January 2025
**Lecture Topic:** Terraform Syntax and Modules

## 1. HCL (HashiCorp Configuration Language)
Key blocks in Terraform.

### Provider Block
Specifies the cloud provider.
```hcl
provider "aws" {
  region = "us-east-1"
}
```

### Resource Block
The actual component to create.
```hcl
resource "aws_instance" "my_server" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "DevOps-Server"
  }
}
```

## 2. Variables
Input variables allow parameterization.
```hcl
variable "region" {
  default = "us-east-1"
}
```

## 3. State Management
Terraform stores state in `terraform.tfstate`.
> [!IMPORTANT]
> Never commit `terraform.tfstate` to Git if it contains secrets. Use Remote State (S3 + DynamoDB) for teams.
