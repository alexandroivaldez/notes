# Terraform Notes
**Terraform** - A declarative cloud agnostic infrastructure as code tool. It is used with multiple cloud providers: AWS, Azure, VMSphere, etc.

**State File** - the single course of truth of your infrastructure. It reflects what's actually on your cloud.

**Installing Terraform on Mac**
```
brew install hashicorp/tap/terraform
brew update
brew upgrade hashicorp/tap/terraform
```
## Terraform Code

***Initializes Terraform state***
``` tf
terraform init
```

***Validates your code's syntax***
```
terraform validate
```

***Format your code***
```
terraform fmt
```

***See Changes***
```
terraform plan
```

***Apply Changes***
```
terraform apply
```

***Destroy Your Infrastructure***
```
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


