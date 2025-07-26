# 1. Login to Azure CLI
az login

# 2. Create a user in Azure AD
az ad user create \
  --display-name "<Display-Name>" \
  --user-principal-name "<username>@<yourdomain>.onmicrosoft.com" \
  --password "<YourPassword>" \
  --force-change-password-next-login true

# 3. Create a group
az ad group create \
  --display-name "<Group-Name>" \
  --mail-nickname "<mail-nickname>"

# 4. Add user to the group
az ad group member add \
  --group "<Group-Name>" \
  --member-id $(az ad user show --id "<username>@<yourdomain>.onmicrosoft.com" --query id -o tsv)

# 5. Get your subscription ID (if needed)
az account show --query id -o tsv

# 6. Assign Reader role to user or group on the subscription
az role assignment create \
  --assignee <object-id> \
  --role Reader \
  --scope /subscriptions/<subscription-id>
