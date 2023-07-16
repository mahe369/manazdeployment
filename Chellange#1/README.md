Terraform code to deploy three-tier architecture on azure

Deplyment Statement

1. One virtual network tied in three subnets.
2. Each subnet will have one virtual machine.
3. First virtual machine -> allow inbound traffic from internet only.
4. Second virtual machine -> entertain traffic from first virtual machine only and can reply the same virtual machine again.
5. App can connect to database and database can connect to app but database cannot connect to web.

The Terraform resources will consists of following structure

```
├── main.tf                   // The primary entrypoint for terraform resources.
├── vars.tf                   // It contain the declarations for variables.
├── output.tf                 // It contain the declarations for outputs.
├── terraform.tfvars          // The file to pass the terraform variables values.
```

Module

1. resourcegroup - creating RG
2. networking - creating azure Vnet and subnets
3. securitygroup - creating network security group, setting desired security rules and associating them to subnets
4. compute - creating availability sets, network interfaces and VM
5. database - creating DB server


To run the code you need to append the variables in the terraform.tfvars

Each module consists minimum two files: main.tf, vars.tf

resourcegroup and networking modules consists of one extra file named output.tf

Deployment Steps
terraform init
terraform plan`
terraform validate
terraform apply
-----End-----
validates the configuration files in a directory, referring only to the configuration and not accessing any remote services such as remote state, provider APIs, etc

**Step 3** `terraform apply`

used to apply the changes required to reach the desired state of the configuration
