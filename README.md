# Azure VM ansible provisioner on Github Actions
### You will need:
1. Active Azure subscription
2. Github account (Github Actions is awesome, try it!)

### Go!
1. Go to https://portal.azure.com 
2. Open cloud shell and run
```
az ad sp create-for-rbac --name "testSP" --sdk-auth --role contributor --scopes /subscriptions/00000000-0000-0000-0000-000000000000
```
where `00000000-0000-0000-0000-000000000000` is your subscription ID

This command will generate JSON that looks like:
```
{
  "clientId": "***",
  "clientSecret": "***",
  "subscriptionId": "***",
  "tenantId": "***",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```

This JSON will be used as the value of `AZURE_CREDENTIALS` in the next steps (save it for now)

2. Fork this repo
3. Create secret environment variables (repository) in forked repo

Project settings -> Secret -> Create secret

![image](https://user-images.githubusercontent.com/87818818/126692197-91db9e42-1708-4571-be03-e468046c5c41.png)

- `AZURE_VM_PASS` = generated pass (keep it strong) 
- `AZURE_CREDENTIALS` = JSON generated previously

4. Go to `Actions` tab and press something like 'Yes, I see, this repo is good, activate it please'

5. Go to `Actions` -> `CreateAzureVM` workflow -> `run workflow`
![image](https://user-images.githubusercontent.com/87818818/126694569-b23d62cc-14b3-4654-a889-04acd2588cfa.png)