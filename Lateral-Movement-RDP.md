# Lateral Movement via Remote Desktop Protocol (RDP)

## Overview
This document details the process of performing **lateral movement** (MITRE ATT&CK Lateral Movement (TA0008) using **Remote Desktop Protocol (RDP)** between two machines on a **personal hotspot network**.
The test was conducted using the following network configuration:

- **Victim laptop**:  IPv4 Address `172.20.10.4`
- **Attacker laptop**:  IPv4 Address `172.20.10.2`

The objective was to establish an RDP session from the **victim laptop** to the **attacker laptop**, capture logs, analyze evidence, and then revert all system settings in the victim machine.

---

## 1. Network Setup
###  Steps Taken:
1. Both devices were connected to a **personal mobile hotspot** to ensure they were on the same subnet.
2. I made sure the victim`s laptop can be pinged, so I enabled the rule "File and Printer Sharing (Echo Request - ICMPv4-In)" in Windows Firewall (as shown in screenshot https://ibb.co/N2tSJXvs)
3. Since I already checked in Command Prompt the IP Adress for each device, I verified next the PING connectivity using:
   ```powershell
   ping 172.20.10.4
   ```
   -  Successful reply confirmed network connectivity. (as shown in screenshot https://ibb.co/hRFZh7cg)

---

## 2. Enabling RDP on the Victim Machine
###  Steps Taken:
1. Opened **Run (`Win + R`)** → Typed `sysdm.cpl` → Enter.
2. Navigated to the **Remote** tab.
3. Enabled:
   -  "Allow Remote Assistance connections to this computer."
   -  "Allow remote connections to this computer." (check screenshot https://ibb.co/WvB00p0j)

---

## 3. Establishing RDP Connection from Attacker to Victim
###  Steps Taken:
1. Opened **Remote Desktop Connection (`mstsc`)** on the attacker laptop.
2. Entered the **victim's IP (`172.20.10.4`)**.
3. Logged in using valid credentials.
4. Successfully established an RDP session. (as shown in the printscreen https://ibb.co/tTYkGYLm)

---

## 4. Captured Lateral Movement Evidence (Event Logs)
###  Steps Taken:
1. Opened **Event Viewer (`eventvwr.msc`)** on the victim machine.
2. Navigated to:
   
   
``` Windows Logs → Security  ```

3. Filtered the logs:
   -  `Event ID 4624` (Successful login)
   -  `Event ID 4672` (Special privileges assigned)
Screenshots: https://ibb.co/GQvMBCm2 & https://ibb.co/dwL5NJ6H

---

## 5. Confirming Active RDP Sessions
###  Steps Taken:
1. On the victim machine, I opened **Command Prompt (`cmd`)**.
2. Then I ran:
   ```powershell
   netstat -an | find ":3389"
   ```
3. I could identify an **active RDP session** with the **target laptop (`172.20.10.2`)**. (check screenshot here https://ibb.co/tTYkGYLm)

---

## 6. Reverted the System Changes

---

 **Best practices against lateral movement**: 
-  Restricting Remote Desktop Protocol
- Adopting Principle of Least Privilege  rule
- Separating the systems using different VLANs
- Enabling Network Level Authentication

---
