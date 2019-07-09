# Modern data warehouse resource manager templates
[![Deploy to Azure](https://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/http%3A%2F%2Fraw.githubusercontent.com%2Fwmeints%2Fmodern-datawarehouse%2Fmaster%2Fazuredeploy.json)

This repository contains a set of resource manager templates to quickly deploy a modern data warehouse to Azure.
Please note that these templates are here for demonstration purposes. You have to design the layout 
of your data lake and configure the permissions for each component yourself. The default set up is safe, but might not fit your company.

Interesting in learning more about setting up a modern data warehouse? [Contact Info Support](ai@infosupport.com)!

## Deploying the data warehouse
There are two methods of deployment, you can either use the Deploy to azure button at the top of this file.
Or you can follow the steps defined below to deploy your data warehouse.

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
First, clone the repository to disk and modify the `parameters.json` file so it matches your situation.
Then, using the following command, deploy the resources to azure:

```
az group create <resource-group-name>
az group deployment create -g <resource-group-name> --parameters @parameters.json --template-uri https://raw.githubusercontent.com/wmeints/modern-datawarehouse/master/azuredeploy.json
```

Replace the resource group name with the name of the resource group you want to deploy to.
