# ARM and ARM Templates

This is the demo arm template from the talk on Azure Resource Manager.

There is instructions provided to deploy this template 3 ways.

 - Through the Azure Portal
 - Powershell
 - Azure ClI

## Portal

Please follow these instructions to deploy from the azure portal
<https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-deploy-portal>

## Powershell

### Installing Azure Powershell Cmdlets

See here to install azure powershell cmdlets
<https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps?view=azurermps-5.3.0>

### Deploying templates using powershell

1. Login to azure

```powershell
Login-AzureRmAccount
```

2. Set your subscription

```powershell
Select-AzureRmSubscription -SubscriptionName <yourSubscriptionName>
```

3. Create a resource group if it doesn't already exist

```powershell
New-AzureRmResourceGroup -Name ExampleGroup -Location ”Australia Southeast”
```

4. Deploy the Arm template to the resource group

```powershell
New-AzureRmResourceGroupDeployment `
    -Name ExampleDeployment `
    -ResourceGroupName ExampleGroup `
    -TemplateFile template.json `
    -TemplateParameterFile params.test.json `
    -Mode Complete `
    -Force `
    -Verbose
```

## Azure CLI

A set of python tools to manange azure. Works cross platform.

### Installing the CLI

See here for instruction on installing the azure cli
<https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest>

### Deploying using the CLI

1. Login to azure

```bash
az login
```

2. Create a resource group if it doesn't exists already

```bash
az group create --name ExampleGroup --location "Australia Southeast”
```

3. deploy the template.

```bash
az group deployment create \
       --name ExampleDeployment \
       --resource-group ExampleGroup \
       --template-file template.json \
       --parameters @params.test.json \
       --mode Complete \
       --verbose
```