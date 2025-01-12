<p align="center">
  <img src="https://github.com/Jalal-Hatamleh/AD-Azure/blob/main/images/1.png?raw=true" alt="Installation Screenshot"/>
</p>

# Cloud-Based Deployment of On-Premises Active Directory in Azure

In this hands-on lab, I set up an Active Directory environment in Microsoft Azure. I created a Domain Controller (DC) VM and a Client VM, with the goal of simulating an on-premises Active Directory setup in the cloud. First, I configured the necessary network resources, then deployed a Windows Server 2022 VM ("DC-1") with a static IP, and disabled its firewall for testing connectivity. Afterward, I created a Windows 10 VM ("Client-1"), set its DNS to point to the Domain Controller's IP, and tested the connection by pinging the DC and verifying the DNS settings.

## Technologies and Tools Used

- **Microsoft Azure (Virtual Machines/Compute)**
- **Remote Desktop**
- **Active Directory Domain Services**
- **PowerShell**

## Operating Systems Deployed

- **Windows Server 2022**
- **Windows 10 Pro (Version 22H2)**

## Step-by-Step Guide to Deployment and Configuration

### Setting Up the Domain Controller in Azure

1. **Create a Resource Group**: I started by creating a resource group in Azure to organize the resources and ensure efficient management.
2. **Set Up a Virtual Network and Subnet**: I then created a Virtual Network and subnet to host the infrastructure for both the Domain Controller and Client VMs.
3. **Deploy the Domain Controller VM**: I created a Windows Server 2022 VM called "DC-1" to serve as the Domain Controller.
   - Username: `jalal-lab-ad`
   - Password: `Password123!`
4. After the VM was deployed, I set the Domain Controller’s NIC Private IP address to be static, ensuring that the IP remained fixed for DNS resolution.
5. To make sure everything was working smoothly, I logged into the VM and temporarily disabled the Windows Firewall to test connectivity.

![Installation Screenshot](https://github.com/Jalal-Hatamleh/AD-Azure/blob/main/images/2.png?raw=true)

### Setting Up the Client-1 VM in Azure

1. **Deploy Client-1 VM**: I then created a Windows 10 VM called "Client-1" to simulate a client machine in the Active Directory network.
   - Username: `jalal-lab-ad`
   - Password: `Password123!`
2. I made sure that Client-1 was deployed in the same region and Virtual Network as DC-1 to ensure they could communicate.
3. Once the VM was ready, I configured Client-1’s DNS settings to point to DC-1’s static IP, so it could resolve domain names properly.

![Installation Screenshot](https://github.com/Jalal-Hatamleh/AD-Azure/blob/main/images/3.png?raw=true)

### Verifying Connectivity

1. From the Azure portal, I restarted the Client-1 VM to ensure it applied all new settings.
2. I logged into Client-1 and tried pinging DC-1’s private IP address to check for connectivity.
   - The ping was successful, confirming that the machines could communicate over the network.
3. I opened PowerShell on Client-1 and ran `ipconfig /all` to verify the DNS settings.
   - I made sure the DNS settings were correctly pointing to DC-1’s private IP, confirming that Client-1 could resolve the Domain Controller.

![Installation Screenshot](https://github.com/Jalal-Hatamleh/AD-Azure/blob/main/images/4.png?raw=true)

## Key Takeaways: Real-world Experience with Active Directory in Azure

- **Azure Resource Setup**: I gained hands-on experience in setting up Resource Groups, Virtual Networks, and Subnets in Azure, giving me a solid foundation for cloud infrastructure management.
- **Domain Controller Configuration**: I deployed a Windows Server 2022 VM as a Domain Controller in Azure and configured it with a static IP for DNS resolution.
- **DNS Configuration**: I set up DNS on Client-1 to point to the Domain Controller's static IP, ensuring proper domain name resolution.
- **Firewall and Connectivity Testing**: I disabled the Windows Firewall on DC-1 for initial testing, then confirmed connectivity by pinging and checking the DNS settings with `ipconfig /all`.
- **PowerShell for Verification**: I used PowerShell to verify DNS resolution and ensure that the network connection between DC-1 and Client-1 was functioning as expected.

---
