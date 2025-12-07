<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

# Preparing Active Directory in Azure

## Environments and Technologies Used
- Microsoft Azure (Resource Groups, Virtual Networks, Virtual Machines)
- Remote Desktop Protocol (RDP)
- Windows Server Manager
- DNS Configuration Tools
- Command-Line Networking Tools (ping, ipconfig)

## Operating Systems Used
- Windows Server (Domain Controller)
- Windows 10 (Client Machine)

## Objectives
- Create the foundational Azure environment for Active Directory  
- Configure a Domain Controller (DC-1) with a static private IP  
- Connect a client machine (Client-1) to the AD environment  
- Modify DNS settings to support domain communication  
- Test network reachability and DNS resolution  
- Establish the prerequisites for installing and joining Active Directory  

# Core Configuration Overview


## Azure Resources Created  
The first thing I did was create the basic pieces that the environment needs: a resource group and a virtual network.  
The resource group keeps every part of this environment organized in one place.  
The virtual network allows my virtual machines to talk to each other privately.


<img width="951" height="841" alt="image" src="https://github.com/user-attachments/assets/ff10dd91-03bc-4551-91dd-b15543d646ed" />


Why this matters:  
This shows I can organize cloud resources correctly and set up a private network, which is essential for Active Directory to work.


## Domain Controller (DC-1) Setup  

I created a resource group called active-directory-lab. I also created  two virtual machines named DC-1 (windows server) and Client-1 (windows 10). The windows server will become the Domain Controller. I also set its private IP address to static so it never changes.


<img width="1535" height="435" alt="image" src="https://github.com/user-attachments/assets/36b325e5-325f-4de7-9e8c-5d6e205fe355" />
<img width="583" height="611" alt="image" src="https://github.com/user-attachments/assets/4a391d9e-c355-47f1-8b54-75749ec3bcaf" />


Why this matters:  
The domain controller must always keep the same IP address because every computer in the domain depends on it.


## Firewall Adjustments for Testing  

After logging into DC-1 through Remote Desktop, I turned off the firewall temporarily. This is only for early testing so that basic communication works with no interference. In a real environment, the firewall stays on, but this lab focuses on building the foundation first.



<img width="1044" height="795" alt="image" src="https://github.com/user-attachments/assets/52d1f058-815e-43e5-a40a-c022a989ae3f" />


Why this matters:  
This confirms the environment is allowed to send simple network traffic while testing connectivity.


## Client Machine (Client-1) Setup

Next I changed the DNS setting of client-1 so that this computer would use DC-1 as its DNS server. Active Directory depends heavily on DNS, so this step is required.


<img width="1533" height="1023" alt="image" src="https://github.com/user-attachments/assets/cf345b7b-e00a-454f-a384-46fb1e9cf645" />


Why this matters:  
Active Directory will not work unless the client computer knows how to find the domain controller through DNS.


## Restarting Client-1  

After changing DNS, I restarted Client-1 from the Azure portal so the network changes would fully apply.


<img width="1533" height="1019" alt="image" src="https://github.com/user-attachments/assets/9796e0a7-8528-44e2-81b8-7aca43a78167" />


Why this matters:  
Restarting ensures the new DNS settings are active.


## Connectivity and DNS Testing  
When Client-1 came back online, I logged in and tested communication between the two machines. First, I used the “ping” command to see if Client-1 could reach DC-1’s private IP. Then I ran “ipconfig /all” to confirm that Client-1 was using DC-1 as its DNS server.


<img width="858" height="729" alt="image" src="https://github.com/user-attachments/assets/54923f7f-ef4d-494f-b89e-01e26b18a171" />


Why this matters:  
This proves that the network and DNS are set up correctly, which is required before Active Directory can be fully installed and joined.


## Skills Demonstrated throughout project:
- Setting up a private network so computers can talk to each other in the cloud  
- Configuring a server to act as the “main controller” for an organization  
- Adjusting network and DNS settings so machines can locate the controller  
- Using basic troubleshooting tools like ping and ipconfig to verify everything works  
- Understanding the foundational steps needed before installing Active Directory


Summary  
This project shows that I understand how to build the core pieces of an Active Directory environment from scratch in Azure. These skills are used in real IT jobs when creating test environments, supporting hybrid cloud networks, or preparing new systems for employees.
