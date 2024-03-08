# Azure Remediation

## Introduction
In this project, I implemented some NIST 800-53 and Microsoft Cloud Security Benchmark Recommendations to harden our environment. This includes implementing Azure Firewall, configuring Azure private link for Key Vault & Storage Instances, & associating subnets with a network security group. After setting up the SOC environment in Azure initially, our Cloud Security Benchmark Score was only about 41%, it would go up to about 77% after the implementations. This project is related to my other project in which I built a SOC/Honeynet in Azure.


## Implementing Azure Private Link for Key Vault Steps:

Go to Azure Key Vault:

![Go to azure key vault](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/ccedfcc7-9718-4745-bfdb-243dd03197cd)

After accessing the key vault, go to Networking:

![Go to networking](https://github.com/James-Jeudy/AzureRemediation/assets/160562010/a2b4f560-b245-4171-be99-1724f21368af)

In firewalls & virtual networks, make sure public access is disabled & Allow Trusted Microsoft services to bypass this firewall is enabled:
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

Afterwards, you need to remote into your Virtual Machine to make sure that the key vault & store account private links return a private IP Address:

Getting IP Address to remote into Windows VM:
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

## 








Vulnerable Windows 10 Machine with Malicious Software Installed:
![Vulnerable Windows Virtual Machine](https://github.com/James-Jeudy/OpenVAS_Vulnerability-Management/assets/160562010/59df9074-f883-41da-bf4f-1a225679ae78)

## Scanning & Reporting:
Adding Vulnerable Windows 10 Machine via Private IP Address to OpenVAS for unauthenticated scan:
![Adding Windows 10 Machine to OpenVAS for uncredentialed scan](https://github.com/James-Jeudy/OpenVAS_Vulnerability-Management/assets/160562010/2a360f5a-d87b-4c59-9ddb-b10aa19d2306)

Unauthenticated Scan Vulnerabilities:
![Uncredentialed Scan Vulnerabilities](https://github.com/James-Jeudy/OpenVAS_Vulnerability-Management/assets/160562010/f3b9547d-bf85-4408-97e4-92664ff3a807)

After running the unauthenticated scan, I decided to setup a credentialed scan on the machine shown here:
![Credentialed Scan Setup](https://github.com/James-Jeudy/OpenVAS_Vulnerability-Management/assets/160562010/7bb7d1eb-49fb-4a0e-b87c-c1726f35b4b5)

Here are the results of the credentialed scan, It picked up a lot of vulnerabilities in comparison to the unauthenticated scan:
![Credentialed Scan 2](https://github.com/James-Jeudy/OpenVAS_Vulnerability-Management/assets/160562010/6f5d66e8-9a2f-4ca8-a22d-880fdb91b719)

After the scan returned the results, I decided to uninstall the malicious software from the Windows 10 Machine. These were the results afterwards:
![Cleaned up Credential Scan](https://github.com/James-Jeudy/OpenVAS_Vulnerability-Management/assets/160562010/4c3c5807-dd02-472b-bcd6-665767188cc5)

## Conclusion:
This project was a great learning experience as it gave me exposure to OpenVAS, & more exposure to Azure. The OpenVAS & Windows 10 machines were both configured in Azure. I was able to make use of tools to help improve my knowledge and continue the great journey of learning cybersecurity. The tools in this project taught me how to effectively scan, confirm, and remediate vulnerabilities on a machine. Overall, this was a great introduction to Vulnerability Management. 
