# The Basics

Terraform uses HashiCorp Language (HCL) to define your infrastructure as code.

## Fundamental Commands

**terraform init** - is used to initialize a Terraform working directory. It prepares your project by downloading the necessary provider plugins and sets up Terraform for your specific configuration.

```shell
terraform init
```

**terraform plan** - is used to create an execution plan. It analyzes your Terraform configuration files, checks the current state of your infrastructure (based on the state file), and then calculates and displays the actions Terraform will take to achieve the desired state defined in your configuration.

```shell
terraform plan
```

**terraform validate** - is used to check your Terraform configuration files for syntax errors and potential issues. It verifies that your configuration files are correctly written and can be parsed by Terraform.

```shell
terraform validate
```

**terraform fmt** - is used to format your Terraform configuration files in a consistent and readable style. It helps ensure that your code adheres to a specific coding style and follows best practices.

```shell
terraform fmt
```

**terraform apply** - is used to apply the changes defined in your Terraform configuration to your infrastructure. It creates, updates, or deletes resources as necessary to achieve the desired state.

```shell
terraform apply
```

**terraform destroy** - is used to destroy all the resources created by your Terraform configuration. It's essential to clean up resources when they are no longer needed to avoid incurring unnecessary costs.

```shell
terraform destroy
```

## Provider

A provider allows you to interact with a specific cloud or service provider, such as AWS, Azure, Google Cloud, or others. Each provider has its own set of resources and data sources that you can manage using Terraform. To use a provider, you need to configure it in your Terraform configuration file (usually main.tf or split into multiple .tf files).

For example, if you're working with AWS, you would configure the AWS provider like this:

``` shell
provider "aws" {
    region = "us-east-1"
}
```

The code block above specifies that you want to use the AWS provider and set the region to "us-east-1"

## Resource

Resources are the fundamental building blocks of your infrastructure in Terraform. They represent the various components you want to create and manage, such as virtual machines, databases, networks, security groups, and more. Resources are declared in your Terraform configuration and tied to a specific provider.

Here's an example of defining an AWS EC2 instance resource:

``` shell
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}

```

In the example above, we're using the AWS provider to create an EC2 instance. The resource type is aws_instance, and we've named it "example." We specify the Amazon Machine Image (AMI) and the instance type.

## Variables

Variables in Terraform allow you to parameterize your configurations, making them more flexible and reusable. Instead of hardcoding values, you can define variables and then reference them in your resource declarations.

Here's an example of defining and using a variable:

```shell
variable "instance_type" {
  description = "The type of EC2 instance"
  default     = "t2.micro"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = var.instance_type
}

```

In the example above, we've defined a variable called instance_type with a default value of "t2.micro." We then use this variable in the aws_instance resource declaration.

## Outputs

Outputs in Terraform allow you to retrieve and display information about your resources after they've been created or modified. This can be useful for getting important data like IP addresses, DNS names, or other resource attributes.

Here's an example of defining an output:

```shell
output "instance_ip" {
  value = aws_instance.example.private_ip
}
```

In the example above, we're creating an output named instance_ip that retrieves the private IP address of the EC2 instance we created earlier.