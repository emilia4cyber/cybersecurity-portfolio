# Exposing Threat Behavior with Any.Run Sandbox  

## About the Project  
This project demonstrates my ability to detect and analyze malware using Any.Run, uncovering hidden functionalities and attack vectors. 

I simulated a real-world malware intrusion by analyzing a malicious document extracted from an infected .zip file via MalwareBazaar.  

## Top Findings:

###  Process & Registry Activity  
- The malware executed via **WinRAR**
- Registry modifications detected in `HKEY_CURRENT_USER\SOFTWARE\WinRAR\ArcHistory`, a potential persistence technique.  

###  File & Network Analysis  
- **Malicious File:** `2ec35da14989692e77df25d56c7b1d43a3e93a72ec2fc7cce67b2fa448744752.xlsm`  
- **Indicators of Compromise (IOCs):** File hashes & suspicious registry changes.  
- **Network Activity:** Outbound connections to **ocsp.digicert.com**, **crl.microsoft.com**, and other domains, potentially for C2 communication.  

##  Security Recommendations  
- Use **Wireshark** to monitor DNS & HTTP(S) traffic for anomalies.  
- Set up **real-time alerts** for registry modifications.  
- Integrate findings with **SIEM** for proactive threat detection.

