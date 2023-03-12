Pre -requesites

Install terraform <--> AZ cli <--> git

login to the Azure CLI using:
# az login

list the Subscriptions associated with the account via:
# az account list

set subscription id for session 
# az account set --subscription="insert the ID output via command "az account list"

create Service Principle 
# az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/"insert the ID output via command "az account list"

These values map to the Terraform variables like so:

# appId is the client_id defined above.
# password is the client_secret defined above.
# tenant is the tenant_id defined above.

Login with the newly created Service Principle.
# az login --service-principal -u CLIENT_ID -p CLIENT_SECRET --tenant TENANT_ID

 list the VM sizes by specifying an Azure region.
# az account list-locations
# az vm list-sizes --location westus

When storing the credentials as Environment Variables, for example:

# sh
export ARM_CLIENT_ID="00000000-0000-0000-0000-000000000000"
export ARM_CLIENT_SECRET="12345678-0000-0000-0000-000000000000"
export ARM_TENANT_ID="10000000-0000-0000-0000-000000000000"
export ARM_SUBSCRIPTION_ID="20000000-0000-0000-0000-000000000000"
# PowerShell
> $env:ARM_CLIENT_ID = "00000000-0000-0000-0000-000000000000"
> $env:ARM_CLIENT_SECRET = "12345678-0000-0000-0000-000000000000"
> $env:ARM_TENANT_ID = "10000000-0000-0000-0000-000000000000"
> $env:ARM_SUBSCRIPTION_ID = "20000000-0000-0000-0000-000000000000"

Created Terraform Providers.
providers.tf using azurerm provider.