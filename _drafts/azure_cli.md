---
layout: post
title:  "Azure CLI"
categories: Azure
---
Przydatne komendy do automatyzacji zadań z Azure CLI.

```
az login
az interactive # interactive mode
az account list-locations
az group list
az group delete --name group-wfh
```

:wink:

## Wykorzystane komendy
Tworzenie `Resource Group`
```
az group create --location northeurope --name group-wfh
```

Tworzenie `Functions App`
```
func init LocalFunctionProj --typescript
cd LocalFunctionProj
func new --name HttpExample --template "HTTP trigger"
npm install
npm start
func start
```

Tworzenie `Storage Account` na potrzeby `Functions App`
```
az storage account create --resource-group  group-wfh --name storagewfh
az storage account create --name <STORAGE_NAME> --location westeurope --resource-group AzureFunctionsQuickstart-rg --sku Standard_LRS
```

Tworzenie `Functions App`
```
az functionapp create --resource-group group-wfh --storage-account storagewfh --consumption-plan-location northeurope --runtime node --runtime-version 10 --functions-version 3 --name sentimentwfh
```

Budowanie aplikacji produkcyjnej
```
npm run build:production 
func azure functionapp publish sentimentwfh
```

Tworzenie `Cognitive Services`
```
az cognitiveservices account  create --kind CognitiveServices --location northeurope --sku S0 --resource-group group-wfh --name cognitivewfh
```

Tworzenie `CosmosDB`
```

```

# Common commands

| Resource type | Azure CLI command group |
|---------------|-------------------------|
| [Resource group](/azure/azure-resource-manager/resource-group-overview) | [az group](/cli/azure/group) |
| [Virtual machines](/azure/virtual-machines) | [az vm](/cli/azure/vm) |
| [Storage accounts](/azure/storage/common/storage-introduction) | [az storage account](/cli/azure/storage/account) |
| [Key Vault](/azure/key-vault/key-vault-whatis) | [az keyvault](/cli/azure/keyvault) |
| [Web applications](/azure/app-service) | [az webapp](/cli/azure/webapp) |
| [SQL databases](/azure/sql-database) | [az sql server](/cli/azure/sql/server) |
| [CosmosDB](/azure/cosmos-db) | [az cosmosdb](/cli/azure/cosmosdb) |
| Functions | [az functionapp](https://docs.microsoft.com/en-us/cli/azure/functionapp?view=azure-cli-latest) |
| Cognitive Services | [az cognitiveservices](https://docs.microsoft.com/en-us/cli/azure/cognitiveservices?view=azure-cli-latest)  |

# Func templates
```
Azure Blob Storage trigger
Azure Cosmos DB trigger
Durable Functions activity
Durable Functions HTTP starter
Durable Functions orchestrator
Azure Event Grid trigger
Azure Event Hub trigger
HTTP trigger
IoT Hub (Event Hub)
Azure Queue Storage trigger
SendGrid
Azure Service Bus Queue trigger
Azure Service Bus Topic trigger
SignalR negotiate HTTP trigger
Timer trigger
```

# Locations
```json
[
  {
    "displayName": "East Asia",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/eastasia",
    "latitude": "22.267",
    "longitude": "114.188",
    "name": "eastasia",
    "subscriptionId": null
  },
  {
    "displayName": "Southeast Asia",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/southeastasia",
    "latitude": "1.283",
    "longitude": "103.833",
    "name": "southeastasia",
    "subscriptionId": null
  },
  {
    "displayName": "Central US",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/centralus",
    "latitude": "41.5908",
    "longitude": "-93.6208",
    "name": "centralus",
    "subscriptionId": null
  },
  {
    "displayName": "East US",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/eastus",
    "latitude": "37.3719",
    "longitude": "-79.8164",
    "name": "eastus",
    "subscriptionId": null
  },
  {
    "displayName": "East US 2",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/eastus2",
    "latitude": "36.6681",
    "longitude": "-78.3889",
    "name": "eastus2",
    "subscriptionId": null
  },
  {
    "displayName": "West US",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/westus",
    "latitude": "37.783",
    "longitude": "-122.417",
    "name": "westus",
    "subscriptionId": null
  },
  {
    "displayName": "North Central US",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/northcentralus",
    "latitude": "41.8819",
    "longitude": "-87.6278",
    "name": "northcentralus",
    "subscriptionId": null
  },
  {
    "displayName": "South Central US",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/southcentralus",
    "latitude": "29.4167",
    "longitude": "-98.5",
    "name": "southcentralus",
    "subscriptionId": null
  },
  {
    "displayName": "North Europe",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/northeurope",
    "latitude": "53.3478",
    "longitude": "-6.2597",
    "name": "northeurope",
    "subscriptionId": null
  },
  {
    "displayName": "West Europe",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/westeurope",
    "latitude": "52.3667",
    "longitude": "4.9",
    "name": "westeurope",
    "subscriptionId": null
  },
  {
    "displayName": "Japan West",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/japanwest",
    "latitude": "34.6939",
    "longitude": "135.5022",
    "name": "japanwest",
    "subscriptionId": null
  },
  {
    "displayName": "Japan East",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/japaneast",
    "latitude": "35.68",
    "longitude": "139.77",
    "name": "japaneast",
    "subscriptionId": null
  },
  {
    "displayName": "Brazil South",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/brazilsouth",
    "latitude": "-23.55",
    "longitude": "-46.633",
    "name": "brazilsouth",
    "subscriptionId": null
  },
  {
    "displayName": "Australia East",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/australiaeast",
    "latitude": "-33.86",
    "longitude": "151.2094",
    "name": "australiaeast",
    "subscriptionId": null
  },
  {
    "displayName": "Australia Southeast",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/australiasoutheast",
    "latitude": "-37.8136",
    "longitude": "144.9631",
    "name": "australiasoutheast",
    "subscriptionId": null
  },
  {
    "displayName": "South India",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/southindia",
    "latitude": "12.9822",
    "longitude": "80.1636",
    "name": "southindia",
    "subscriptionId": null
  },
  {
    "displayName": "Central India",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/centralindia",
    "latitude": "18.5822",
    "longitude": "73.9197",
    "name": "centralindia",
    "subscriptionId": null
  },
  {
    "displayName": "West India",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/westindia",
    "latitude": "19.088",
    "longitude": "72.868",
    "name": "westindia",
    "subscriptionId": null
  },
  {
    "displayName": "Canada Central",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/canadacentral",
    "latitude": "43.653",
    "longitude": "-79.383",
    "name": "canadacentral",
    "subscriptionId": null
  },
  {
    "displayName": "Canada East",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/canadaeast",
    "latitude": "46.817",
    "longitude": "-71.217",
    "name": "canadaeast",
    "subscriptionId": null
  },
  {
    "displayName": "UK South",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/uksouth",
    "latitude": "50.941",
    "longitude": "-0.799",
    "name": "uksouth",
    "subscriptionId": null
  },
  {
    "displayName": "UK West",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/ukwest",
    "latitude": "53.427",
    "longitude": "-3.084",
    "name": "ukwest",
    "subscriptionId": null
  },
  {
    "displayName": "West Central US",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/westcentralus",
    "latitude": "40.890",
    "longitude": "-110.234",
    "name": "westcentralus",
    "subscriptionId": null
  },
  {
    "displayName": "West US 2",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/westus2",
    "latitude": "47.233",
    "longitude": "-119.852",
    "name": "westus2",
    "subscriptionId": null
  },
  {
    "displayName": "Korea Central",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/koreacentral",
    "latitude": "37.5665",
    "longitude": "126.9780",
    "name": "koreacentral",
    "subscriptionId": null
  },
  {
    "displayName": "Korea South",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/koreasouth",
    "latitude": "35.1796",
    "longitude": "129.0756",
    "name": "koreasouth",
    "subscriptionId": null
  },
  {
    "displayName": "France Central",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/francecentral",
    "latitude": "46.3772",
    "longitude": "2.3730",
    "name": "francecentral",
    "subscriptionId": null
  },
  {
    "displayName": "France South",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/francesouth",
    "latitude": "43.8345",
    "longitude": "2.1972",
    "name": "francesouth",
    "subscriptionId": null
  },
  {
    "displayName": "Australia Central",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/australiacentral",
    "latitude": "-35.3075",
    "longitude": "149.1244",
    "name": "australiacentral",
    "subscriptionId": null
  },
  {
    "displayName": "Australia Central 2",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/australiacentral2",
    "latitude": "-35.3075",
    "longitude": "149.1244",
    "name": "australiacentral2",
    "subscriptionId": null
  },
  {
    "displayName": "UAE Central",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/uaecentral",
    "latitude": "24.466667",
    "longitude": "54.366669",
    "name": "uaecentral",
    "subscriptionId": null
  },
  {
    "displayName": "UAE North",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/uaenorth",
    "latitude": "25.266666",
    "longitude": "55.316666",
    "name": "uaenorth",
    "subscriptionId": null
  },
  {
    "displayName": "South Africa North",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/southafricanorth",
    "latitude": "-25.731340",
    "longitude": "28.218370",
    "name": "southafricanorth",
    "subscriptionId": null
  },
  {
    "displayName": "South Africa West",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/southafricawest",
    "latitude": "-34.075691",
    "longitude": "18.843266",
    "name": "southafricawest",
    "subscriptionId": null
  },
  {
    "displayName": "Switzerland North",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/switzerlandnorth",
    "latitude": "47.451542",
    "longitude": "8.564572",
    "name": "switzerlandnorth",
    "subscriptionId": null
  },
  {
    "displayName": "Switzerland West",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/switzerlandwest",
    "latitude": "46.204391",
    "longitude": "6.143158",
    "name": "switzerlandwest",
    "subscriptionId": null
  },
  {
    "displayName": "Germany North",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/germanynorth",
    "latitude": "53.073635",
    "longitude": "8.806422",
    "name": "germanynorth",
    "subscriptionId": null
  },
  {
    "displayName": "Germany West Central",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/germanywestcentral",
    "latitude": "50.110924",
    "longitude": "8.682127",
    "name": "germanywestcentral",
    "subscriptionId": null
  },
  {
    "displayName": "Norway West",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/norwaywest",
    "latitude": "58.969975",
    "longitude": "5.733107",
    "name": "norwaywest",
    "subscriptionId": null
  },
  {
    "displayName": "Norway East",
    "id": "/subscriptions/0687e951-9acf-47da-88f3-16d530ada8de/locations/norwayeast",
    "latitude": "59.913868",
    "longitude": "10.752245",
    "name": "norwayeast",
    "subscriptionId": null
  }
]
```