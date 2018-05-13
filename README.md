# Kubernetes Repo
This repo contains an AKS ARM template to use Managed Kubernetes clusters and integrate them with custom VNETs

## AKS-AdvancedNetworking-Template
This directory contains an ARM parameter and template file.  
You must update subnet ids, key vault secrets and id.
Make sure you create a service principal with contributor permissions on the Azure subscription you want to use to deploy this template. Add the key of the created service principal as a secret in Azure Keyvault.
Following URL gives more details about the service principal: [https://github.com/Azure/acs-engine/blob/master/docs/serviceprincipal.md]()

The template requires an OMS workspace (this workspace is not automatically created by this template). 
It will add the container solution to the workspace and configures the deployed AKS cluster with the necessary OMS agents on the cluster nodes.

Deploy the template using Azure RM Powershell or Azure CLI. After the deployment is finished, you have to use Azure CLI to configure your local kubectl config file. Use following command to automatically configure your local kubectl config file:

`az aks generate-credentials -n <name of your aks> -g <resource group name in which aks is deployed> `

### Kubectl
You need kubectl to be able to work on the deployed kubernetes cluster. Use following URL how to install kubectl on Linux/MacOS/Windows manually:
[https://kubernetes.io/docs/tasks/tools/install-kubectl/]()

You can also use Azure CLI to install kubectl:

`az aks install-cli`

Another option is Azure Cloud Shell, which already has kubectl preinstalled.

### Example App
You can deploy following demo app on your AKS cluster:
[https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough#run-the-application]()


