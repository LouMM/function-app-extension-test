# function-app-extension-test
 
This will create a dynamic function app ready for extension testing.

## One-time setup
1. [Intall the Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) and log in. Run `az login` and follow the instructions.
2. You may need to specify the subscrition. Run `az acount set -s SUBSCRIPTION` where "SUBSCRIPTION" is a subscription name or subscription ID.
3. Make sure Web Apps knows how to deploy from GitHub. Manually connect this repo to a test site in the portal and perform the authorization for your account.

## Setup the test
2. Clone the repo and cd to it.
3. Create a resource group in West US 2. Run `az group create -l WestUS2 -n GROUPNAME` where "GROUPNAME" is a name you provide. That value will be used again later
4. Deploy the template. Run `az group deployment create -n TestDeployment -g GROUPNAME --template-file function-app-for-extension-template.json`.

The template should pull contents from the **FunctionApp** folder in the GitHub repo.

Now you can run your tests.

## Teardown

1. Delete the resource group. Run `az group delete -n GROUPNAME`.