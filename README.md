# Azure_Terraform_LB
This is an exercise for SimpliLearn Microsoft Certified Azure Administrator course end project 2.

The content is taken from "Quickstart: Create a public load balancer using Terraform"

https://learn.microsoft.com/en-us/azure/load-balancer/quickstart-load-balancer-standard-public-terraform
Follow the steps in the above article to try this out.

Usage:
provider.tf -- specifies Azure as the cloud provider
main.tf -- to create needed resources such as resource grouop, virtual network, subnet, network security group and rules, public IP, network interface, virtual machines (Linux servers with extension to install Nginx web server), load balancer front-end, load balancer back-end pool, load balancer probe (of healthy servers in the back-end pool).
variables.tf -- to specify names for the resources to be created.  This allows code reusability (e.g. using main.tf for another infrastructure).
outputs.tf -- url for users to specify, when accessing web content.

Steps (in Azure console):
1. Initialize Terraform: terraform init -upgrade
2. Create a Terraform execution plan: terraform plan -out main.tfplan
3. Apply a Terraform execution plan: terraform apply main.tfplan
4. check that the resources have been created.
5. Verify the front-end public IP: echo $(terraform output -raw public_ip_address)
6. When done, create an execution plan to clean up the resources: terraform plan -destroy -out main.destroy.tfplan
7. Apply the clean up plan: terraform apply main.destroy.tfplan
