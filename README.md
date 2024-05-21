# MSP-LAN-

---
This document details my knowledge of creating a Local Area Network (LAN) for a small Managed Service Provider (MSP).

---
STAGE 0

![STAGE 0 drawio (1)](https://github.com/BlazWilson/MSP-LAN-/assets/170445236/d08e00aa-4c10-4a21-905d-df3a76f3f706)

This is the network before installation of other switches or routers.

---
STAGE 1

![Stage 1 drawio](https://github.com/BlazWilson/MSP-LAN-/assets/170445236/21317d16-f1e5-4e3f-8c63-d6a72c955274)

In this stage, I added a Fortinet firewall, 2 ethernet switches, and a windows 10 workstation
From there: 
Link the WAN port on the firewall to the WAN-SWITCH.
Link the LAN port on the firewall to the LAN-SWITCH.
Link the DMZ port on the firewall to the DMZ-SWITCH.
Link the Win10 workstation to the LAN-SWITCH.

---
STAGE 2

![STAGE 2 drawio](https://github.com/BlazWilson/MSP-LAN-/assets/170445236/81ace8a6-8893-4a63-9eff-ba46dae2f8c5)

![Screenshot 2024-05-21 155928](https://github.com/BlazWilson/MSP-LAN-/assets/170445236/ebcbc22c-dc51-4c2c-bb6b-8870f79b9feb)

In this screenshot, we had to set a static IP address for our network adapter. The reason a static IP address was needed was because for our network we can't have the IP address changing everytime the adapter turns on and connects to the internet. When information travels to our network and pings our server, traffic will be lost if the IP address is constantly changing using DHCP.

![Screenshot 2024-05-21 155952](https://github.com/BlazWilson/MSP-LAN-/assets/170445236/f2dc514d-325a-4381-9d08-26447c48b375)

Step 1 : Add a Win2012r2 server to the lab workspace.
Step 2 : Link the Win2012r2 server to the LAN-SWITCH
Step 3 and 4 : After setting our static IP address, subnet mask, and default gateway; along with our DNS Server. I had to ping the google.com server to ensure that the DNS server was responding to requests. I pinged 8.8.8.8 (google.com) to ensure there was connectivity to the internet from our IP address.
Step 5 and 6 : of this process consisted of me setting up an active directory service to create user accounts (12 total) 2 per user in my group. An admin and an user account.

---
STAGE 3

![STAGE 3 drawio](https://github.com/BlazWilson/MSP-LAN-/assets/170445236/6fb1101d-3c8e-4ad9-b3e5-c9939cd3d107)

Step 1 : As you can see I added another windows server, linked it to the LAN switch.

![Screenshot 2024-05-21 164710](https://github.com/BlazWilson/MSP-LAN-/assets/170445236/4d653f49-2d7e-4621-aa77-e497ff563a9b)

Step 2 : In this server I assigned another static IP address to the new server with the same subnet mask and default gateway. I changed the DNS 1 IP address due to the domain controller acts as the internal DNS server. So if windows2012r2-2 has a request, it reaches out to Windows server 2012r2-1, if win2012r2-1 server doesn't have the DNS query asked for, win2012r2-1 reaches out to the router/firewall who then asks 8.8.8.8 or google.com if they have the answer. After that I Synced the time using NTP (network time protocol).
Installed IIS webserver on windows server and joined the server to the domain. 

---


