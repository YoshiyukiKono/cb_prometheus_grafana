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
