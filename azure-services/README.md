# Dev-lab Azure Services

## What does it create ?

1. sql-database.tf deploy [SQL Database](https://azure.microsoft.com/en-us/services/sql-database/) and 2 databases.
2. service-bus.tf deploy [Service bus](https://azure.microsoft.com/en-us/services/service-bus/).

## Required Tooling

- [Terraform](https://www.terraform.io/)
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)

## Running

1. Login to the Azure CLI using `az login` (Skip this if you using cloud shell)
2. Clone this repository and cd into the directory
3. Create a varaibles.tfvars file and add your variables

Example: `variables.tfvars`

```tf
resource_id = "<yourname_nospaces>"

# Optional
admin_login = "" (Default:dbadmin)
admin_password = "" (Default:Passw0rd123!)
resource_group_name = "" (Default:devlab-services)
resource_group_location = ""  (Default:southeastasia)
queue_name = "" (Default:audit_queue)
compute_database_name = "" (Default:ComputeDB)
audit_database_name = "" (Default:AuditDB)
```

4. Alternatively, variables can be populated via CLI using `var` flag .

```sh
terraform plan -var "resources_id=<yourname_nospaces>" -out=azure-services.tfplan
```

5. Run `terraform init` then `terraform plan` to see what will be created, finally if it looks good run `terraform apply`

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
