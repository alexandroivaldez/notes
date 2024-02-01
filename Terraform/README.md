# Terraform Notes

## Terraform

Terraform is a declarative, cloud-agnostic infrastructure as code (IaC) tool used to manage and automate the provision of resources across multiple cloud providers such as AWS, Azure, and VMWare's vSphere.

## Why?

Terraform allows you to implement software development methodologies within your cloud infrastructure management, including practices like code reviews and version control."

Terraform is inherently *cloud-agnostic*, which means it isn't tied to a particular cloud provider. With Terraform, you can define infrastructure configurations for multiple cloud providers, ensuring you have the flexibility to avoid vendor lock-in and choose the best-suited cloud services for your needs.

Terraform also allows you to automate provisioning. You can spin up and spin down infrastructure resources quickly and efficiently, ensuring that your cloud environment scales to meet the demands of your applications and workloads.

- This automation not only saves time but also helps maintain consistency in your infrastructure, reducing the risk of configuration errors and improving overall system reliability.

## How?

Terraform Core takes the terraform state and the terraform config file and collaborates with a provider that takes our state and config and figures out how to give us exactly what we want in the cloud.

State File

- Terraform's representation of the world
- It's a JSON file containing detailed information about every resource and data object that you deploying using TerraForm.
- Contains sensistive information (e.g. password) so it must be protected.
- Can be stored locally or remotely.

Local Backend

- Terraform state stored inside of a computer.
- Pros:
  - Easy to set up
- Cons:
  - Sensisitive values in plain text
  - Manual
  - Uncollaborative

Table of Contents

1. [The Basics](terraform-basics.md)
2. [Managing State](terraform-state.md)
3. Variables and Modules
4. Version Control
5. [Meta-Arguments](terraform-metaArgs.md)

**Official Documentation**
- [Terraform Documentation](https://developer.hashicorp.com/terraform?ajs_aid=8f071fb2-75a4-430c-9e20-c1b2d4d15110&product_intent=terraform)