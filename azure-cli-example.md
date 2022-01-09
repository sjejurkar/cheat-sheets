# Azure CLI examples
## Download  Azure App Service logs
```
az login
# switch to desired directory if you have access to more than one Directories
# for Azure CLI subscription=directory
export SUBSCRIPTION_ID=my-azure-directory-id
az account set --subscription $SUBSCRIPTION_ID
export RESOURCE_GROUP=my-resource-group
export APP_SVC_NAME=my-app-service-name
export LOG_ZIP=$APP_SVC_NAME_logs.zip
# list app services
az webapp list --resource-group $RESOURCE_GROUP
# download app service files to local disk
az webapp log download --log-file $LOG_ZIP  --resource-group $RESOURCE_GROUP --name $APP_SVC_NAME
```
