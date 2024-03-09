# Azure Remediation(NIST 800-53 & Microsoft Cloud Security Benchmark)

## Introduction
In this project, I implemented some NIST 800-53 controls and Microsoft Cloud Security Benchmark Recommendations to harden my SOC environment. This includes implementing Azure Firewall, configuring Azure private link for Key Vault & Storage Instances, associating subnets with a network security group, & enabling MFA. After setting up the SOC environment in Azure initially, our Cloud Security Benchmark Score was only about 41%, it would go up to about 77% after the implementations. This project is related to my other project, [Creating a Live SOC/Honeynet in Azure ](https://github.com/James-Jeudy/SOC-Honeynet-Azure).

![Nist 800-53 Picture](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/aa2029d1-58bb-4ea2-a3fb-223786d49525)





## Implementing Azure Private Link for Key Vault:

Go to Azure Key Vault:

![Go to azure key vault](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/ccedfcc7-9718-4745-bfdb-243dd03197cd)

After accessing the key vault, go to Networking:

![Go to networking](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/a2b4f560-b245-4171-be99-1724f21368af)




In firewalls & virtual networks, make sure public access is disabled & Allow Trusted Microsoft services to bypass this firewall is enabled & apply changes:
![Switch to disable public access, allow trusted microsoft services to bypass this firewall then click apply](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/b83b2090-843b-4b96-9fc0-9b387ded382b)

Afterwards, create the private endpoint connections:
![Create private endpoint connections](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/48f05a9c-6d92-438b-9825-298b6e3081a0)
![Create private endpoint connection 2](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/055f6501-9ffd-4e2e-b932-9424c13ff4ed)
![Create private endpoint connection 3](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/841b7928-4388-4651-9a4d-a324ce73fc49)
![Create private endpoint connection 4](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/2d258152-2a2e-49ed-926f-e0b8f5c66c57)
![create private endpoint connection DNS](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/3ebaafc5-ab63-40a1-ad60-0e29c07f9d50)
![Create private link azure key vault](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/4f8f888f-892e-464c-93ab-81e84327de29)
![Your deployment is complete endpoint](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/3260fc23-5a27-49f1-9b58-65f193539537)



## Implementing Azure Private Link for Storage Account Steps:

Go to Storage accounts:
![Enable Private Link Storage Account](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/22e9411b-9c91-4550-b15f-29250d4542ca)



Make sure configuration settings are set up properly:
![Enable private link storage account 2](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/69ffb0f7-8285-4233-b9e8-969e14816627)

Afterwards, go to Networking & make sure Public network access is disabled and then save:
![Go to networking then disable public network access](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/67131073-05f6-4aab-bb77-74850f090213)

Go to private endpoints connections and create one:
![Create private endpoint](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/b0a25a45-2935-41ed-bdaa-0aa28e2fe0ae)
![Create private endpoint part one](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/824c224a-df95-4888-827f-c062f7572df3)
![Make sure to block blob storage](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/77f9d77a-bfb7-483d-b6e3-6becf329c3be)
![Fine to leave as is and then click Next](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/7e63df79-ef25-4f7c-9a76-0d8514b1002f)
![Just make sure subscription and Resource group are accurate](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/2ab18b33-d64b-4dd3-8a90-042f240e0ebd)
![Create private endpoint for storage account final step](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/291c791f-9b6d-4da3-9e58-e934a4596680)
![Completed Deployment for storage account private endpoint](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/ff4c0f7c-874a-48d9-8652-ad71f9bdf559)

## Confirming Private Links are configured properly for Storage Account & Key Vault:


Retrieving IP Address to remote into Windows VM:
![Remote into Windows VM to test private links](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/8e5dc660-151f-4f77-be69-581c62d5761a)

Copy the Key Vault URL:
![Grab Azure Key Vault URL](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/873b341c-d423-4c18-86e7-813184dc84f3)

Run an nslookup command on the Azure Key Vault URL:

![Run NSLookup of KeyVault Address](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/f83d0a13-33cf-43cc-ba2b-66e0a48cf95e)
![NSLookup Key Vault Cyberlab results private IP Address](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/77f8d427-73c4-41a6-9a20-b169f55cb020)

Go to Endpoints under the storage account section and then retrieve the primary endpoint name for blob service:
![Gather storage account endpoint information to check private link](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/ad12e3a7-af48-4863-8b19-f41198529a0b)

Run an nslookup command on the storage account to make sure it returns a Private IP Address:
![Nslookup for storage account resolves to Private IP Address](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/d28398d3-7cfc-470c-a523-b0a832817701)

## Adding a network security group to a Subnet:

Create Network Security Groups:
![Create network security group to attach to subnet](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/406ae0db-addd-4214-9872-6187b6380341)

![Create network security group to add to subnet 2](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/c27b447c-72e0-4e10-8ccd-ba731edf93f5)

Go to Virtual networks and select your V-Net:
![Go to V-net to add subnet](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/971629f7-3a92-40cf-9457-875199aa36bb)

Go to Subnets & select default:
![Subnet settings vnet](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/f978fa70-2b84-4790-a1b6-b62bc3bdbded)
Add the network security group:
![Configured network security group](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/1f25e8ac-f62e-40c7-9662-32b8d6209ca5)

## Adding multiple owners to subscriptions:
![Adding more than one owner to subscription account](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/4c2f4d20-e922-4810-a7bf-97ef3762784b)

Manual Remediation Steps & Unhealthy Resource:
![Adding more than one owner to subscription account 2](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/cfe40775-ec56-45d7-9dbb-8667bcd72077)

Go to IAM & Add Role Assignment:
![Add role assignment Azure](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/aa979bd5-eca2-4e7d-adda-66af8d9c730c)

Go to Privileged administrator roles and click Owner:
![Add user to owner role](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/607a6584-aba3-4181-92b3-25a31c6cb4b1)

Add Assignment:
![Add another assignment](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/ad57b2e3-a8e4-4d51-8675-2572c1829d11)

Add Members:
![Adding another user](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/95f96fb3-80c3-461f-9ee5-ac5150d28c7f)

![Review   Assign Role](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/742b886f-054f-4117-a186-b61dc6edf5c3)

## Enabling MFA per user in Azure:
![Enable MFA part 1](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/ebf2a0bc-3c20-42d3-bb5e-a42d827dd774)

Go to All Users and then Per-user MFA:
![Go to per user mfa](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/6eb78518-b097-43b7-8e94-b82a16e1f857)

Bulk update all the users and then click Enable. This may take multiple attempts to enable for all users:
![Pick every user   bulk update to enable](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/80eeff04-0422-4a95-bff9-69aa8460d0e5)

![Enable MFA for all users](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/a94c2054-41b3-4a4b-a6d4-6d61cc9db1cd)

![Afterwards MFA should now be enabled](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/8a0270e7-ba74-44f2-a622-9c808976858c)

## Deploying Azure Firewall on a V-Net:
![Configure Firewall Settings](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/6732eade-fcef-46d6-a989-bf928948dc2e)

Go to configure Azure Firewall:
![Configure Azure Firewall](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/7a83f5ac-bdd9-41aa-a62f-364928dd48b3)

![Creating Azure Firewall Part One](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/5ed1ce66-9abf-4769-9e1f-5163348ca64e)
![Creating Azure Firewall Part Two](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/3493f7b4-e1d4-4992-968c-10396da150d1)
![Azure Firewall Deployment](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/69f38156-00e3-48d8-b308-23eeb4be73a0)
![RGCyberlab Deploy Firewall Success](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/a0c720d1-d9a9-4bb3-b2db-88131edcc603)
![Successful Deployment of Azure Firewall](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/021ee83d-53e5-4326-93c7-0c0271594b52)





![Secure Score   Recommendations](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/d1fd7f01-24cc-4ead-a47f-c077e7493b91)



## Conclusion:

