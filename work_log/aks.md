```
REML0693:~ yoshiyuki.kono$ brew install azure-cli
Updating Homebrew...
==> Auto-updated Homebrew!
Updated 2 taps (homebrew/core and homebrew/cask).
==> Updated Formulae
Updated 2162 formulae.
==> New Casks
nocturn                                                                pb
==> Updated Casks
aerial                             djay-pro                           missive                            screen
alt-tab                            duet                               nextcloud                          segger-embedded-studio-for-arm
anki                               elpass                             nosqlbooster-for-mongodb           sensei
anybar                             epichrome                          nrlquaker-winbox                   silentknight
aquaskk                            exodus                             nuclear                            snipaste
beatunes                           extraterm                          ocenaudio                          stats
beekeeper-studio                   feishu                             oolite                             studiolinkstandalone
blitz                              freesmug-chromium                  openmsx                            superproductivity
brave-browser                      fsnotes                            pagico                             supertuxkart
busycal                            futuniuniu                         popo                               swiftformat-for-xcode
busycontacts                       grids                              proclaim                           tableplus
c0re100-qbittorrent                hstracker                          propresenter                       telegram
cabal                              icollections                       prowritingaid                      terminus
cacher                             icq                                proxyman                           thunderbird
chromedriver                       id3-editor                         publish-or-perish                  trilium-notes
chromium                           kafka-tool                         pycharm-ce-with-anaconda-plugin    typora
clash-for-windows                  kubernetic                         pycharm-with-anaconda-plugin       vidrio
cleanmymac                         lark                               qiyimedia                          webtorrent
clipgrab                           lifesize                           quail                              whale
cookie                             lockrattler                        receipts                           whatsapp
craftmanager                       loom                               redisinsight                       wormhole
cryptomator                        mailmate                           remember-the-milk                  yojimbo
daedalus-mainnet                   marvin                             remote-desktop-manager             yyets
datadog-agent                      microsoft-azure-storage-explorer   remote-desktop-manager-free        zeplin
decrediton                         mini-program-studio                runjs

==> Downloading https://homebrew.bintray.com/bottles/azure-cli-2.11.1.catalina.bottle.tar.gz
==> Downloading from https://d29vzk4ow07wi7.cloudfront.net/6b0558080c5ad02b243bb6a5823f687374251ee0ba4028bdddc3717c2d7eaca8?response-content-
######################################################################## 100.0%
==> Pouring azure-cli-2.11.1.catalina.bottle.tar.gz
==> Caveats
Bash completion has been installed to:
  /usr/local/etc/bash_completion.d
==> Summary
🍺  /usr/local/Cellar/azure-cli/2.11.1: 15,371 files, 194.8MB
REML0693:~ yoshiyuki.kono$ az login
You have logged in. Now let us find all the subscriptions to which you have access...
[
  {
    "cloudName": "AzureCloud",
    "homeTenantId": "897b2d61-f537-4fde-bc07-520be26839d8",
    "id": "f855d6ab-cda7-485b-8360-7146658961e2",
    "isDefault": true,
    "managedByTenants": [],
    "name": "240 - SE EMEA",
    "state": "Enabled",
    "tenantId": "897b2d61-f537-4fde-bc07-520be26839d8",
    "user": {
      "name": "yoshiyuki.kono@couchbase.com",
      "type": "user"
    }
  }
]
REML0693:~ yoshiyuki.kono$ az account list --output table
Name           CloudName    SubscriptionId                        State    IsDefault
-------------  -----------  ------------------------------------  -------  -----------
240 - SE EMEA  AzureCloud   f855d6ab-cda7-485b-8360-7146658961e2  Enabled  True
REML0693:~ yoshiyuki.kono$ az group create --name myResourceGroup --location eastus
{
  "id": "/subscriptions/f855d6ab-cda7-485b-8360-7146658961e2/resourceGroups/myResourceGroup",
  "location": "eastus",
  "managedBy": null,
  "name": "myResourceGroup",
  "properties": {
    "provisioningState": "Succeeded"
  },
  "tags": null,
  "type": "Microsoft.Resources/resourceGroups"
}
REML0693:~ yoshiyuki.kono$ az network vnet create -g myResourceGroup -n myAKSVnet  --address-prefix 10.0.0.0/12  --subnet-name myAKSSubnet --subnet-prefix 10.8.0.0/16
{
  "newVNet": {
    "addressSpace": {
      "addressPrefixes": [
        "10.0.0.0/12"
      ]
    },
    "bgpCommunities": null,
    "ddosProtectionPlan": null,
    "dhcpOptions": {
      "dnsServers": []
    },
    "enableDdosProtection": false,
    "enableVmProtection": false,
    "etag": "W/\"a91b4976-8d4b-439a-a973-4d1280eb51d1\"",
    "id": "/subscriptions/f855d6ab-cda7-485b-8360-7146658961e2/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myAKSVnet",
    "ipAllocations": null,
    "location": "eastus",
    "name": "myAKSVnet",
    "provisioningState": "Succeeded",
    "resourceGroup": "myResourceGroup",
    "resourceGuid": "543fc673-78f9-42b9-822d-58ae2298466f",
    "subnets": [
      {
        "addressPrefix": "10.8.0.0/16",
        "addressPrefixes": null,
        "delegations": [],
        "etag": "W/\"a91b4976-8d4b-439a-a973-4d1280eb51d1\"",
        "id": "/subscriptions/f855d6ab-cda7-485b-8360-7146658961e2/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myAKSVnet/subnets/myAKSSubnet",
        "ipAllocations": null,
        "ipConfigurationProfiles": null,
        "ipConfigurations": null,
        "name": "myAKSSubnet",
        "natGateway": null,
        "networkSecurityGroup": null,
        "privateEndpointNetworkPolicies": "Enabled",
        "privateEndpoints": null,
        "privateLinkServiceNetworkPolicies": "Enabled",
        "provisioningState": "Succeeded",
        "purpose": null,
        "resourceGroup": "myResourceGroup",
        "resourceNavigationLinks": null,
        "routeTable": null,
        "serviceAssociationLinks": null,
        "serviceEndpointPolicies": null,
        "serviceEndpoints": null,
        "type": "Microsoft.Network/virtualNetworks/subnets"
      }
    ],
    "tags": {},
    "type": "Microsoft.Network/virtualNetworks",
    "virtualNetworkPeerings": []
  }
}
REML0693:~ yoshiyuki.kono$ subnet_id=$(az network vnet show -g myResourceGroup -n myAKSVnet --query subnets[].id -o tsv)
REML0693:~ yoshiyuki.kono$ az aks create -g myResourceGroup -n myAKSCluster --node-count 3  --vnet-subnet-id $subnet_id --service-cidr 10.0.0.0/16 --dns-service-ip 10.0.0.10 --generate-ssh-keys   --location eastus  --network-plugin azure  --kubernetes-version 1.12.7
Setting vm_set_type to availabilityset as it is             not specified and kubernetes version(1.12.7) less than 1.12.9 only supports             availabilityset

Setting load_balancer_sku to basic as it is not specified and kubernetesversion(1.12.7) less than 1.13.0 only supports basic load balancer SKU

Directory permission is needed for the current user to register the application. For how to configure, please refer 'https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal'. Original error: Insufficient privileges to complete the operation.
REML0693:~ yoshiyuki.kono$ az aks get-versions --location eastus --query orchestrators[].orchestratorVersion -o tsv`
> 
> 
REML0693:~ yoshiyuki.kono$ az aks get-versions --location eastus --query orchestrators[].orchestratorVersion -o ts
az aks get-versions: 'ts' is not a valid value for '--output'. See 'az aks get-versions --help'.

The most similar choice to 'ts' is:
	tsv
REML0693:~ yoshiyuki.kono$ v
-bash: v: command not found
REML0693:~ yoshiyuki.kono$ az aks get-versions --location eastus --query orchestrators[].orchestratorVersion -o tsv
1.15.11
1.15.12
1.16.10
1.16.13
1.17.7
1.17.9
1.18.4
1.18.6
REML0693:~ yoshiyuki.kono$ az aks create -g myResourceGroup -n myAKSCluster --node-count 3  --vnet-subnet-id $subnet_id --service-cidr 10.0.0.0/16 --dns-service-ip 10.0.0.10 --generate-ssh-keys   --location eastus  --network-plugin azure  --kubernetes-version 1.18.6
Directory permission is needed for the current user to register the application. For how to configure, please refer 'https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal'. Original error: Insufficient privileges to complete the operation.
REML0693:~ yoshiyuki.kono$ 

```

```
REML0693:~ yoshiyuki.kono$ az aks install-cli
Downloading client to "/usr/local/bin/kubectl" from "https://storage.googleapis.com/kubernetes-release/release/v1.19.0/bin/darwin/amd64/kubectl"
Please ensure that /usr/local/bin is in your search PATH, so the `kubectl` command can be found.
Downloading client to "/var/folders/d7/9kcy9b615hs7pvfsbrsx84yc0000gp/T/tmp1fun0g6x/kubelogin.zip" from "https://github.com/Azure/kubelogin/releases/download/v0.0.5/kubelogin.zip"
Please ensure that /usr/local/bin is in your search PATH, so the `kubelogin` command can be found.
REML0693:~ yoshiyuki.kono$ az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
The Resource 'Microsoft.ContainerService/managedClusters/myAKSCluster' under resource group 'myResourceGroup' was not found. For more details please go to https://aka.ms/ARMResourceNotFoundFix
```


```
REML0693:Work yoshiyuki.kono$ subnet_id=$(az network vnet show -g myResourceGroup -n myAKSVnet --query subnets[].id -o tsv)
REML0693:Work yoshiyuki.kono$ az aks create -g myResourceGroup -n myAKSCluster --enable-managed-identity --node-count 3  --vnet-subnet-id $subnet_id --service-cidr 10.0.0.0/16 --dns-service-ip 10.0.0.10 --generate-ssh-keys   --location eastus  --network-plugin azure  --kubernetes-version 1.18.6
The cluster is an MSI cluster, please manually grant Network Contributor role to the system assigned identity after the cluster is created, see https://docs.microsoft.com/en-us/azure/aks/use-managed-identity
{- Finished ..
  "aadProfile": null,
  "addonProfiles": {
    "KubeDashboard": {
      "config": null,
      "enabled": false,
      "identity": null
    }
  },
  "agentPoolProfiles": [
    {
      "availabilityZones": null,
      "count": 3,
      "enableAutoScaling": null,
      "enableNodePublicIp": false,
      "maxCount": null,
      "maxPods": 30,
      "minCount": null,
      "mode": "System",
      "name": "nodepool1",
      "nodeLabels": {},
      "nodeTaints": null,
      "orchestratorVersion": "1.18.6",
      "osDiskSizeGb": 128,
      "osType": "Linux",
      "provisioningState": "Succeeded",
      "scaleSetEvictionPolicy": null,
      "scaleSetPriority": null,
      "spotMaxPrice": null,
      "tags": null,
      "type": "VirtualMachineScaleSets",
      "vmSize": "Standard_DS2_v2",
      "vnetSubnetId": "/subscriptions/f855d6ab-cda7-485b-8360-7146658961e2/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myAKSVnet/subnets/myAKSSubnet"
    }
  ],
  "apiServerAccessProfile": null,
  "autoScalerProfile": null,
  "diskEncryptionSetId": null,
  "dnsPrefix": "myAKSClust-myResourceGroup-f855d6",
  "enablePodSecurityPolicy": null,
  "enableRbac": true,
  "fqdn": "myaksclust-myresourcegroup-f855d6-537e13cf.hcp.eastus.azmk8s.io",
  "id": "/subscriptions/f855d6ab-cda7-485b-8360-7146658961e2/resourcegroups/myResourceGroup/providers/Microsoft.ContainerService/managedClusters/myAKSCluster",
  "identity": {
    "principalId": "27be11e4-6a73-4249-8fb7-d8d50baa623e",
    "tenantId": "897b2d61-f537-4fde-bc07-520be26839d8",
    "type": "SystemAssigned"
  },
  "identityProfile": {
    "kubeletidentity": {
      "clientId": "93d0b26d-7a2f-47a2-98f2-65876b781bad",
      "objectId": "ce5cd7e7-efb3-4a2d-83b3-097cbb0205f1",
      "resourceId": "/subscriptions/f855d6ab-cda7-485b-8360-7146658961e2/resourcegroups/MC_myResourceGroup_myAKSCluster_eastus/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myAKSCluster-agentpool"
    }
  },
  "kubernetesVersion": "1.18.6",
  "linuxProfile": {
    "adminUsername": "azureuser",
    "ssh": {
      "publicKeys": [
        {
          "keyData": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDVqR5jolvnP4KDVyj948+jBOzje8rMtahcOWTkzFmPTKTt6GrgYSxT6Z1raLQrWwxGa3IFrJ+jQarcr8kde0Tr0v6PJcLjryRiilYhZu3Zvs2u+BjX0nEVv8rQ7HJAuLIvLq141U8dOecnCmrqKdGopni1xmmDALuv+ies/IMsvikP7pKOGRC8KGfUtOPnyNJ7EY65h4LO+cOT9AyikX36dBvWvs0sdmWfanj0d2pqe8cfaEiL8801Um46HNtO1JH9aVTizS6oFyD0YKqcbT4g1QgD/PpogLg5Ke0qFMp14E1Ld5tt+qkrsF5lkc4jSOyqmE9iL5QKN1Sr0TIVJJRA/P2GVn0jdLsbmDfDBek35gu+BtNaXggyJpoN9FLDnd8ta1mmYu3NQ9oTacoMwfAmDNtOFjfG9ZRY/C2jD8y64Tvdkb2AN3CBe4/uQD0JMzG6/oqBYLM/kH9Q20283TksxTBa9OdAg3A5aZ7ApmkzzyDpuu4/idePYYjI1FwHtD0= yoshiyuki.kono@REML0693\n"
        }
      ]
    }
  },
  "location": "eastus",
  "maxAgentPools": 10,
  "name": "myAKSCluster",
  "networkProfile": {
    "dnsServiceIp": "10.0.0.10",
    "dockerBridgeCidr": "172.17.0.1/16",
    "loadBalancerProfile": {
      "allocatedOutboundPorts": null,
      "effectiveOutboundIps": [
        {
          "id": "/subscriptions/f855d6ab-cda7-485b-8360-7146658961e2/resourceGroups/MC_myResourceGroup_myAKSCluster_eastus/providers/Microsoft.Network/publicIPAddresses/0fe37d3c-87e9-42db-9bd0-e2a14173784c",
          "resourceGroup": "MC_myResourceGroup_myAKSCluster_eastus"
        }
      ],
      "idleTimeoutInMinutes": null,
      "managedOutboundIps": {
        "count": 1
      },
      "outboundIpPrefixes": null,
      "outboundIps": null
    },
    "loadBalancerSku": "Standard",
    "networkMode": null,
    "networkPlugin": "azure",
    "networkPolicy": null,
    "outboundType": "loadBalancer",
    "podCidr": null,
    "serviceCidr": "10.0.0.0/16"
  },
  "nodeResourceGroup": "MC_myResourceGroup_myAKSCluster_eastus",
  "privateFqdn": null,
  "provisioningState": "Succeeded",
  "resourceGroup": "myResourceGroup",
  "servicePrincipalProfile": {
    "clientId": "msi",
    "secret": null
  },
  "sku": {
    "name": "Basic",
    "tier": "Free"
  },
  "tags": null,
  "type": "Microsoft.ContainerService/ManagedClusters",
  "windowsProfile": {
    "adminPassword": null,
    "adminUsername": "azureuser"
  }
}
REML0693:Work yoshiyuki.kono$ 
```
```
