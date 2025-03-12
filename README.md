# XG Firewall | Site-to-Site RED tunnel LAB

## Objective

The primary goal of this Sophos XGS-Firewall v21.0 LAB is to set up a site-to-site RED tunnel between two Sophos Firewall devices without deploying a RED device. In this configuration, one firewall acts as the server and the other as the client.

### Job Skills Learned

- Deploying SD-RED devices to securely extend networks across remote locations.
- Adding a static route.
-  Adding firewall rules for tunnel traffic.
- Network Segmentation & Routing
- Cybersecurity & Compliance


### Tools Used

- Sophos XGS Firewall v21.0 device (or virtual instance) in virtualized environments (VMware).
- An SD-RED 20/60 device (or simulation setup)
- Access to the Sophos Central Management Portal
- SFOS 21.0 Web Interface (GUI)
- SFOS 21.0 Command Line Interface (CLI)
- Control Center Dashboard: Built-in monitoring tool for real-time traffic and event analysis.
- Backup and Restore Tools
- Traffic Generation Tools
- EVE-NG for simulating network devices (e.g., routers, PCs, or switches) to test


*Ref 1: Network Diagram*
![image](https://github.com/user-attachments/assets/a8ed3fef-11fb-4f8a-97a4-52c2cd50194c)

## CONFIGURATION STEPS


### Add a RED interface on the Firewall RED Server

The Firewall RED Server listens for incoming connections, and the Firewall RED Client initiates the outgoing connection. Translating the Firewall RED Server's address may interfere with incoming connections. We recommend that you don't use NAT for the Firewall RED Server.
![image](https://github.com/user-attachments/assets/cb252f38-7d7b-44e9-913e-fcc57ae80bb3)
 

-	1. On the Firewall RED Server, go to System services > RED and turn on the RED provisioning service.
 ![image](https://github.com/user-attachments/assets/006e0f17-a970-4d1e-8f6f-110ae161bb29)

-	2. Go to Network > Interfaces, click Add interface, and click Add RED.
 ![image](https://github.com/user-attachments/assets/18720f52-8520-4527-8a9c-6b950bb2af4a)

-	3. Configure as follows:
 ![image](https://github.com/user-attachments/assets/50332208-9e54-41a0-839a-b2860322bcca)
![image](https://github.com/user-attachments/assets/fbfb58e0-efe2-45a0-b957-1e4a039a619f)

 
-	4. Click Save.
The firewall generates a provisioning file.
-	5. On the RED interface, click Menu   and download the provisioning file.
 ![image](https://github.com/user-attachments/assets/01a1ba14-17bc-4348-b000-723199e66b7f)
![image](https://github.com/user-attachments/assets/a0d61dad-cba4-4bcf-8102-717352718c94)
![image](https://github.com/user-attachments/assets/c368367a-1ae1-4359-94b5-f9168f45c1ba)

  
-	6. Copy the file to a network location or removable drive that you can access from the Firewall RED Client.


## Add a RED interface on the Firewall RED Client

-	1. Go to System services > RED and turn on the RED provisioning service.
![image](https://github.com/user-attachments/assets/e71ac4fe-3968-41f2-9a10-6cd030f44dc8)
 
-	2. Go to Network > Interfaces, click Add interface, and click Add RED.
-	3. Configure as follows:
![image](https://github.com/user-attachments/assets/510a8b4a-495f-4556-bfb1-f96033ccbc1c)
![image](https://github.com/user-attachments/assets/bd0da322-aa5d-4486-afb9-33e9a3c557da)
 
 
-	4. Click Save.



## Add static routes

You must configure static routes on both firewalls so that internal networks have a route across the RED tunnel.
-	1. On the Firewall RED Server, go to Routing > Static routes.
-	2. Under IPv4 unicast route, click Add.
-	3. Configure as follows:
 ![image](https://github.com/user-attachments/assets/500fd7df-0e30-44a8-ae75-d55b8c8c4933)

-	4. Click Save.
-	5. On the Firewall RED Client, go to Routing > Static routes.
-	6. Under IPv4 unicast route, click Add.
-	7. Configure as follows:
![image](https://github.com/user-attachments/assets/f6cff32e-b8ea-402f-bb5f-5182409ac08b)
 

## Add firewall rule

For traffic to pass between the two firewalls, you must create a LAN-to-LAN or a similar rule on each firewall.
Do as follows on the Firewall RED Server and Firewall RED Client:
-	1. Go to Rules and policies > Firewall rules.
-	2. Select IPv4, click Add firewall rule, and click new firewall rule.
-	3. Configure as follows:
![image](https://github.com/user-attachments/assets/ea3f20e4-3862-443c-980e-7028557f7d8a)
![image](https://github.com/user-attachments/assets/8e951d9f-2266-44d1-9037-743da140fa6e)

-	4. Click Save
![image](https://github.com/user-attachments/assets/3f000051-2b9f-4472-bd2a-f3e7928766a2)
 





