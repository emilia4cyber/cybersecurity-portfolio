# Windows Locker Ransomware Analysis

## Introduction
This report provides an in-depth analysis of **Windows Locker Ransomware**, a new cyber threat targeting organizations across various industries. 
Using OpenCTI, I have detailed the tactics, techniques, and procedures (TTPs) associated with this ransomware to the MITRE ATT&CK framework, analyzed its Indicators of Compromise (IOC), and provided valuable tips for detection and mitigation.

---

## 1. Threat Intelligence Collection
- **Methodology:**
   - I started my search for recent cybersecurity incidents in the tool OpenCTI
  - I  navigated to **Reports** in OpenCTI and used the keywords: `malware, spyware, ransomware, apt` along with a date filter to identify incidents from the past month (January 2025).
  - I selected the incident **"WINDOWS LOCKER RANSOMWARE"**, which occurred on **January 29, 2025**. (see printscreen [here](https://ibb.co/rfHdxfdn) and [here](https://ibb.co/9mr2PzJB))
- **Background Information:**
  - According to [AlienVault OTX](https://otx.alienvault.com/pulse/6799e67e09b17526ac9ca19a), Windows Locker represents a new type of ransomware strain, which:
    > "Targets victims by encrypting files and appending the `.winlocker` extension. Upon infection, it drops a ransom note named `Readme.txt` with instructions for contacting the attacker. Written in .NET, this sophisticated malware modifies registry keys for persistence, deletes shadow copies, and disables system defenses. It employs AES encryption with a 256-bit key, creates autorun entries, replicates onto removable drives, and disables Windows Defender and Task Manager. The ransomware generates a unique identifier for infected systems, retrieves the local IP address, and includes personalized details in the ransom note. It also modifies the desktop background as part of its psychological impact."
    


## 2. MITRE ATT&CK Mapping and Threat Actor Analysis

  - I started the investigation by checking **Threat Actors** and **Intrusion Sets** in OpenCTI for any known associations with Windows Locker; no direct links were found.
- **MITRE ATT&CK Techniques Identified:**
  - **T1486** - Data Encrypted for Impact  
    *(in this case with AES-256)*
  - **T1112** - Modify Registry  
    *(for persistence)*
  - **T1070.004** - Indicator Removal: File Deletion  
    *(Deletes shadow copies to prevent recovery)*
  - **T1490** - Inhibit System Recovery  
    *(system back-up are deleted)*
  - **T1083** - File and Directory Discovery  
    *(searches in system directories for as much data as possible)*
  - **T1082** - System Information Discovery  
    *(gather info on hostname, OS version, and hardware configurations before attack)*
    
    You can also have a look in the  [screenshot](https://ibb.co/chv6kM0R) with the MITRE ATT&CK mappings in OpenCTI (section knowledge) 

---

## 3. Indicator of Compromise (IOC) Analysis
- **IOCs Collected from OpenCTI and AlienVault OTX:**
  - **File Hashes:**
    - **File Hash MD5:** `5c86de54f31352ead8d2b3e573ea42fd`
    - **File Hash SHA256:** `1f32f454ba32de5e0b7ed429b3542cdb0a9f826f5f5146f206baf074ec1abfe0`
    - **URL:** `http://y2kid.xyz/mainpage/internets.jpg`
    - **Domain:** `y2kid.xyz`
    Screenshot attached [here](https://ibb.co/mFCGNS41)! 

- **Verification results with VirusTotal:** 
    - 52 out of 71 security vendors flagged both hashes as malicious.(check [screenshot](https://ibb.co/jsPpW7r))
    - Only 4 out of 96 vendors flagged domain and URL as malicious, suggesting a possible false positive. (check [screenshot](https://ibb.co/mFh330Vt))
---

## 4. Detection and Mitigation Strategies against Windows Locker Ransomware

- **Detection Techniques:**
  - Using an up-to-date Endpoint Detection and Response (EDR) system to block .NET-based malware or ransomware like Windows Locker.
  - Monitor Windows Event Logs.
  - Implementing tools like Splunk for detecting patterns associated with the “Windows Locker” ransomware
  
- **Mitigation Strategies:**
  - Sensitive or critical data to be well isolated from external networks (this could include back-up systems as well)
  - Regularly update and patch systems to remediate any vulnerability which  Windows Locker can exploit.

---

## Conclusion
- Windows Locker ransomware adopt advanced techniques for encryption, persistence, and defense evasion.
- As SOC analysts we would have to adopt different approaches against this type of threat: EDR, SIEM, network segmentation, clear incident response plans.


