# OpenVAS Vulnerability Management

## Introduction
In this project, I used Microsoft Azure to setup and configure OpenVAS as my vulnerability scanner to get some experience in vulnerability management. In my environment, I setup OpenVAS as my vulnerability scanner on a Linux VM and used a Windows 10 Virtual Machine as the PC to be scanned. On the Windows 10 VM, some outdated software was installed and the firewall was temporarily turned off. The old software included an old version of Adobe Reader, VLC Player, & Mozilla Firefox. Two different scans were ran on the Windows 10 machine. One was an unauthenticated scan and the other was a credentialed scan.

![OpenVAS Environment](https://github.com/James-Jeudy/OpenVAS_Vulnerability-Management/assets/160562010/2a745819-116b-43c9-871e-6f388f880fcb)

## Lab Environment:
Deployment of OpenVAS Machine:
![OpenVAS deployed](https://github.com/James-Jeudy/OpenVAS_Vulnerability-Management/assets/160562010/a31d3c89-419c-4f4f-85c1-5540b2141acc)

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
