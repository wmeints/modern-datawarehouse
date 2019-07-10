# Modern data warehouse resource manager templates
This repository contains a set of resource manager templates to quickly deploy a modern data warehouse to Azure.
Please note that these templates are here for demonstration purposes. You have to design the layout 
of your data lake and configure the user permissions for each component yourself. 

Interested in learning more about setting up a modern data warehouse? [Contact Info Support](ai@infosupport.com)!

## Deploying the data warehouse
Follow the instructions to deploy the resources to Azure.

### Prerequisites
Please have the following components on your machine: 

* [Azure CLI 2.0](https://docs.microsoft.com/nl-nl/cli/azure/install-azure-cli-macos?view=azure-cli-latest)

### Logging in
Before you can deploy the resource manager template, run the following command in a terminal window:

```
az login
```

Follow the instructions on screen to log in to your Azure account.
After you've logged in, you may need to change the active subscription if you have access to multiple subscriptions.
Use the following command to set the correct subscription:

```
az account set --subscription <subscription-id>
```

### Deploying the resources
Now that you've logged in, you can deploy the templates to production.
First, create a new file `parameters.json` and copy the following content to the file:

```
{
    "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentParameters.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "companyName": {
            "value": "<Insert your companyname here>"
        },
        "environment": {
            "value": "dev"
        }
    }
}
```

Then, modify the contents of the parameter values to fit your needs.
After creating the parameters file, use the following command to deploy the resources to azure:

```
az group create <resource-group-name>
az group deployment create -g <resource-group-name> --parameters @parameters.json --template-uri https://raw.githubusercontent.com/wmeints/modern-datawarehouse/master/azuredeploy.json
```

Replace the resource group name with the name of the resource group you want to deploy to.
