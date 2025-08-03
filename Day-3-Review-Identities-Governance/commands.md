# Create custom role definition JSON file (customrole.json)
# (Created manually with proper JSON content)

# Create the custom role
az role definition create --role-definition customrole.json

# Assign custom role to your user
az role assignment create --assignee "<your-user-principal-name>" --role "Custom Reader Role - Storage Only" --scope /subscriptions/<subscription-id>

# List role assignments (to verify)
az role assignment list --subscription <subscription-id> --output table

# Create resource group (if not exists)
az group create --name Day2-LabRG --location eastus

# Create storage account
az storage account create --name <unique-storage-name> --resource-group Day2-LabRG --location eastus --sku Standard_LRS

# List storage accounts
az storage account list --output table

# Delete role assignment before deleting role
az role assignment delete --assignee "<your-user-principal-name>" --role "Custom Reader Role - Storage Only" --scope /subscriptions/<subscription-id>

# Delete custom role
az role definition delete --name <custom-role-id>

# Delete storage account
az storage account delete --name <storage-account-name> --resource-group Day2-LabRG

# Delete resource group (which deletes all resources inside)
az group delete --name Day2-LabRG --yes --no-wait
