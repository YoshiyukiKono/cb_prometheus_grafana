# AKS

## Install Azure CLI on Mac

https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-macos?view=azure-cli-latest

```
$ brew cask install powershell
$ brew install azure-cli
```

## Install AKS
https://docs.couchbase.com/operator/current/tutorial-aks.html

### Prerequisites
```
$ az login
$ az account list --output table
Name           CloudName    SubscriptionId                        State    IsDefault
-------------  -----------  ------------------------------------  -------  -----------
240 - SE EMEA  AzureCloud   f855d6ab-cda7-485b-8360-7146658961e2  Enabled  True
```
### AKS Setup
Substitute <...>
```
$ az group create --name <myResourceGroup> --location eastus
```
```
$ az network vnet create -g <myResourceGroup> -n <myAKSVnet>  --address-prefix 10.0.0.0/12  --subnet-name <myAKSSubnet> --subnet-prefix 10.8.0.0/16
```
```
$ subnet_id=$(az network vnet show -g <myResourceGroup> -n <myAKSVnet> --query subnets[].id -o tsv)
```

```
$ az aks create -g <myResourceGroup> -n <myAKSCluster> --enable-managed-identity --node-count 3  --vnet-subnet-id $subnet_id --service-cidr 10.0.0.0/16 --dns-service-ip 10.0.0.10 --generate-ssh-keys   --location eastus  --network-plugin azure  --kubernetes-version 1.18.6
```

