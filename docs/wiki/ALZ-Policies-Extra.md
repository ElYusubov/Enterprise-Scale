# ALZ Policies - Extra

This document describes additional ALZ custom policy definitions and initiatives that are not assigned by default in ALZ, but are provided as they may assist some consumers of ALZ in specific scenarios where they can assign these additional policies to help them meet their objectives. We also provide guidance on how to handle certain situations as some of the policies require additional considerations prior to assigning.

> For the complete list of Azure Landing Zones custom policies, please use [AzAdvertizer](https://www.azadvertizer.net/azpolicyadvertizer_all.html), and change `type` to `ALZ`.

## Additional ALZ Custom Policies for consideration

ALZ provides several additional policies that are not assigned by default but that can be used for specific scenarios should they be required.

| Policy | Description | Notes |
|------------|-------------|-------------|
| Deny-Appgw-Without-Waf | Application Gateway should be deployed with WAF enabled | Use to ensure Application Gateways are deployed with Web Application Firewall enabled |
| Deny-Private-Dns-Zones | Deny the creation of private DNS | For organizations that centralize core networking functions, use this policy to prevent the creation of additional Private DNS Zones under specific scopes |
| Deny-Subnet-Without-Udr | Subnets should have a User Defined Route | Should you require all network traffic be directed to an appliance for inspection, you can use this policy to ensure UDR is associated with a subnet |
| Deny-Udr-With-Specific-Nexthop | User Defined Routes with 'Next Hop Type' set to 'Internet' or 'VirtualNetworkGateway' should be denied | Refining `Deny-Subnet-Without-Udr` you can ensure non-compliant UDRs are denied (e.g., bypassing a firewall) |
| Deny-Vnet-Peering | Deny vNet peering | Use to prevent vNet peering under specific scopes (e.g., Sandbox management group) |
| Deny-Vnet-Peering-To-Non-Approved-Vnets | Deny vNet peering to non-approved vNets | Use to control vNet peering under specific scopes, like in the Corp management group, only allow peering to the hub vNet. |
| Deploy-Budget | Deploy a default budget on all subscriptions under the assigned scope | Set a default budget for a specific scope, like setting a $500 budget on all subscriptions in the Sandbox management group |
| Deploy-Vnet-Hubspoke | Deploy Virtual Network with peering to the hub | Automatically peer a new virtual network with the hub, for example, in the Corp management group |
| Deploy-Windows-DomainJoin | Deploy Windows Domain Join Extension with Key Vault configuration | Windows Domain Join a virtual machine using domain name and password stored in Key Vault as secrets |

## 2. ALZ, Workload Specific Compliance and Regulated Industries

The Azure Landing Zone is designed to be a flexible and scalable solution that can be used by organizations in a variety of industries. However, organizations in regulated industries (FSI, Healthcare, etc.) may need to take additional steps to ensure compliance with industry-specific regulations. These regulations often commonly have a consistent set of controls to cover, like CMK, locking down public endpoints, TLS version enforcement, logging etc.

To support the additional control requirements of these industries, we're providing the following additional initiatives that enhance the security and compliance posture of the Azure Landing Zone:

> **Please Note:** These are meant to help customers across all regulated industries (FSI, Healthcare, etc.) and not be aligned to specific regulatory controls, as there are already policy initiatives available for these via [Azure Policy](https://learn.microsoft.com/azure/azure-resource-manager/management/security-controls-policy) & [Microsoft Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/regulatory-compliance-dashboard)

| Initiative ID | Name | Description | # of Policies |
|------------|-------------|-------------|-------------|
| [Enforce-Encryption-CMK](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Encryption-CMK.html) | Deny or Audit resources without Encryption with a customer-managed key (CMK) | This policy initiative is a group of policies that ensures Customer Managed Keys is compliant per regulated Landing Zones. | 30 |
| [Enforce-Guardrails-APIM](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-APIM.html) | Enforce recommended guardrails for API Management | This policy initiative is a group of policies that ensures API Management is compliant per regulated Landing Zones. | 11 |
| [Enforce-Guardrails-AppServices](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-AppServices.html) | Enforce recommended guardrails for App Service | This policy initiative is a group of policies that ensures App Service is compliant per regulated Landing Zones. | 19 |
| [Enforce-Guardrails-Automation](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-Automation.html) | Enforce recommended guardrails for Automation Account | This policy initiative is a group of policies that ensures Automation Account is compliant per regulated Landing Zones. | 6 |
| [Enforce-Guardrails-BotService](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-BotService.html) | Enforce recommended guardrails for Bot Service (service renamed to AI Bot Service) | This policy initiative is a group of policies that ensures Bot Service is compliant per regulated Landing Zones. | 4 |
| [Enforce-Guardrails-CognitiveServices](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-CognitiveServices.html) | Enforce recommended guardrails for Cognitive Services (service renamed to AI Services) | This policy initiative is a group of policies that ensures Cognitive Services is compliant per regulated Landing Zones. | 9 |
| [Enforce-Guardrails-Compute](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-Compute.html) | Enforce recommended guardrails for Compute | This policy initiative is a group of policies that ensures Compute is compliant per regulated Landing Zones. | 2 |
| [Enforce-Guardrails-ContainerApps](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-ContainerApps.html) | Enforce recommended guardrails for Container Apps | This policy initiative is a group of policies that ensures Container Apps is compliant per regulated Landing Zones. | 2 |
| [Enforce-Guardrails-ContainerInstance](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-ContainerInstance.html) | Enforce recommended guardrails for Container Instance | This policy initiative is a group of policies that ensures Container Instance is compliant per regulated Landing Zones. | 1 |
| [Enforce-Guardrails-ContainerRegistry](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-ContainerRegistry.html) | Enforce recommended guardrails for Container Registry | This policy initiative is a group of policies that ensures Container Registry is compliant per regulated Landing Zones. | 12 |
| [Enforce-Guardrails-CosmosDb](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-CosmosDb.html) | Enforce recommended guardrails for Cosmos DB | This policy initiative is a group of policies that ensures Cosmos DB is compliant per regulated Landing Zones. | 6 |
| [Enforce-Guardrails-DataExplorer](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-DataExplorer.html) | Enforce recommended guardrails for Data Explorer | This policy initiative is a group of policies that ensures Data Explorer is compliant per regulated Landing Zones. | 4 |
| [Enforce-Guardrails-DataFactory](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-DataFactory.html) | Enforce recommended guardrails for Data Factory | This policy initiative is a group of policies that ensures Data Factory is compliant per regulated Landing Zones. | 5 |
| [Enforce-Guardrails-EventGrid](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-EventGrid.html) | Enforce recommended guardrails for Event Grid | This policy initiative is a group of policies that ensures Event Grid is compliant per regulated Landing Zones. | 8 |
| [Enforce-Guardrails-EventHub](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-EventHub.html) | Enforce recommended guardrails for Event Hub | This policy initiative is a group of policies that ensures Event Hub is compliant per regulated Landing Zones. | 4 |
| [Enforce-Guardrails-KeyVault-Sup](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-KeyVault-Sup.html) | Enforce additional recommended guardrails for Key Vault | This policy initiative is a group of policies that ensures Key Vault is compliant per regulated Landing Zones. This includes additional policies to supplement Enforce-Guardrails-KeyVault, which is assigned by default in ALZ. | 2 |
| [Enforce-Guardrails-Kubernetes](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-Kubernetes.html) | Enforce recommended guardrails for Kubernetes | This policy initiative is a group of policies that ensures Kubernetes is compliant per regulated Landing Zones. | 16 |
| [Enforce-Guardrails-MachineLearning](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-MachineLearning.html) | Enforce recommended guardrails for Machine Learning | This policy initiative is a group of policies that ensures Machine Learning is compliant per regulated Landing Zones. | 14 |
| [Enforce-Guardrails-MySQL](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-MySQL.html) | Enforce recommended guardrails for MySQL | This policy initiative is a group of policies that ensures MySQL is compliant per regulated Landing Zones. | 2 |
| [Enforce-Guardrails-Network](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-Network.html) | Enforce recommended guardrails for Network and Networking services | This policy initiative is a group of policies that ensures Network and Networking services is compliant per regulated Landing Zones. | 22 |
| [Enforce-Guardrails-OpenAI](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-OpenAI.html) | Enforce recommended guardrails for Azure OpenAI (Cognitive Service) | This policy initiative is a group of policies that ensures Azure OpenAI (Cognitive Services) is compliant per regulated Landing Zones. | 11 |
| [Enforce-Guardrails-PostgreSQL](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-PostgreSQL.html) | Enforce recommended guardrails for PostgreSQL | This policy initiative is a group of policies that ensures PostgreSQL is compliant per regulated Landing Zones. | 1 |
| [Enforce-Guardrails-ServiceBus](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-ServiceBus.html) | Enforce recommended guardrails for Service Bus | This policy initiative is a group of policies that ensures Service Bus is compliant per regulated Landing Zones. | 4 |
| [Enforce-Guardrails-SQL](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-SQL.html) | Enforce recommended guardrails for SQL and SQL Managed Instance | This policy initiative is a group of policies that ensures SQL and SQL Managed Instance is compliant per regulated Landing Zones. | 5 |
| [Enforce-Guardrails-Storage](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-Storage.html) | Enforce recommended guardrails for Storage Account | This policy initiative is a group of policies that ensures Storage is compliant per regulated Landing Zones. | 22 |
| [Enforce-Guardrails-Synapse](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-Synapse.html) | Enforce recommended guardrails for Synapse workspaces | This policy initiative is a group of policies that ensures Synapse is compliant per regulated Landing Zones. | 9 |
| [Enforce-Guardrails-VirtualDesktop](https://www.azadvertizer.net/azpolicyinitiativesadvertizer/Enforce-Guardrails-VirtualDesktop.html) | Enforce recommended guardrails for Virtual Desktop | This policy initiative is a group of policies that ensures Virtual Desktop is compliant per regulated Landing Zones. | 2 |