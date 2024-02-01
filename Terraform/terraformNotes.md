# Terraform Notes

**State File** - the single course of truth of your infrastructure. It reflects what's actually on your cloud.

**Installing Terraform on Mac**

```shell
brew install hashicorp/tap/terraform
brew update
brew upgrade hashicorp/tap/terraform
```

## Terraform Code

***Initializes Terraform state***

```shell
terraform init
```

***Validates your code's syntax***

```shell
terraform validate
```

***Format your code***

```shell
terraform fmt
```

***See Changes***

```shell
terraform plan
```

***Apply Changes***

```shell
terraform apply
```

***Destroy Your Infrastructure***

```shell
terraform destroy
```

## Variables

How to define a variable in Terraform:

```
# vars.tf
variable REGION {
    default = "us-west-1"
}

# providers.tf
providers "aws" {
 region = var.REGION
}
```

## Provisioning

- Build custom images with tools like *packer*
- Use standard Image and use provisioner to setup software and files.
  - File uploads
  - remote_exec
  - Ansible, Puppet or Chef

``` terraform
terraform {
    required_providers {
        aws = {
            source = "hashicorps/aws"
            version = "~> 3.0"
        }
    }
}
```
