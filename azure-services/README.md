# Dev-lab Azure Services

## What does it create ?

The sql-database.tf deploy [SQL Database](https://azure.microsoft.com/en-us/services/sql-database/) and 2 databases.

## Required Tooling

- [Terraform](https://www.terraform.io/)
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)

## Running

1. Login to the Azure CLI az login
2. Clone this repository and cd into the directory
3. Create a varaibles.tfvars file and add your variables

Example: `varaibles.tfvars`

```tf
compute_database_name = "ComputeDB"

audit_database_name = "AuditDB"

admin_login = "dbadmin"

admin_password = "<password>"
```

6. Run `terraform init` then `terraform plan` to see what will be created, finally if it looks good run `terraform apply`

```sh
terraform init
terraform plan -var-file=variables.tfvars -out=azure-services.tfplan
terraform apply azure-services.tfplan
```

## Cleanup

You can cleanup the Terraform-managed infrastructure.

```sh
terraform destroy -var-file=variables.tfvars -force
```