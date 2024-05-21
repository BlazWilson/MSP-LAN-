# MSP-LAN-

---
This document details my knowledge of creating a Local Area Network (LAN) for a small Managed Service Provider (MSP).

---

![STAGE 0 drawio (1)](https://github.com/BlazWilson/MSP-LAN-/assets/170445236/d08e00aa-4c10-4a21-905d-df3a76f3f706)

This is the network before installation of other switches or routers.

---

![Stage 1 drawio](https://github.com/BlazWilson/MSP-LAN-/assets/170445236/21317d16-f1e5-4e3f-8c63-d6a72c955274)

In this stage, I added a Fortinet firewall, 2 ethernet switches, and a windows 10 workstation
From there: 
Link the WAN port on the firewall to the WAN-SWITCH.
Link the LAN port on the firewall to the LAN-SWITCH.
Link the DMZ port on the firewall to the DMZ-SWITCH.
Link the Win10 workstation to the LAN-SWITCH.

---
