# Exposing Threat Behavior with Any.Run Sandbox in a Real World Document

## About the project

This project demonstrates my ability to proactively detect and respond to threats by analyzing malware with Any.Run, uncovering hidden functionalities and attack vectors.

The drive behind this project was to simulate a malware intrusion, to examine the file's behavior, and to extract the key indicators of compromise (IOCs) in a controlled environment.

## Analysis Overview

In this project, I analyzed a real-world malicious document (`2ec35da14989692e77df25d56c7b1d43a3e93a72ec2fc7cce67b2fa448744752.xlsm`) which was extracted from an infected `.zip` file, downloaded from MalwareBazaar screenshot [here](https://ibb.co/DfHNBgSw). 

The document would trigger malicious actions when opened, presenting a clear threat scenario.

Using Any.Run's sandbox environment, I uploaded the document (screenshot [here](https://ibb.co/hx0wGBwh)) and was able to notice the processes, registry activities, file system changes, network connections, and DNS requests initiated by the malicious file. 

This helped me understand how the malware works, assess its potential impact, and its attack lifecycle.

---

### 1. **Process Activity Analysis**

- **Command**: `C:\Program Files\WinRAR\WinRAR.exe` (PID 2076)  
  **Initiating path**: `C:\Users\admin\AppData\Local\Temp\2ec35da14989692e77df25d56c7b1d43a3e93a72ec2fc7cce67b2fa448744752.zip`  
  **Parent Process**: `explorer.exe`  
  **Integrity Level**: Medium  
  **User**: admin  
  **Key Modules**: `comdlg32.dll`, `msvcrt.dll`, `combase.dll`, `rpcrt4.dll`, `shcore.dll`, `shell32.dll`, `advapi32.dll`, `sechost.dll`, `bcrypt.dll`.


- **Key Analysis**: The attack started with WinRAR opening the malicious Excel file. This common trick uses trusted programs to hide malicious actions and to potentially bypass initial security measures. 
The Excel file then ran directly from the archive, showing it uses macros to attack, a typical method.

Relevant screenshots: [1](https://ibb.co/kgZrzBcr), [2](https://ibb.co/27bLx0ZP), [3](https://ibb.co/fdY496mW).

Through this analysis I could prove my abilities in the recognition of common malware deployment strategies and the understanding of initial stages of malware operation.

---

### 2. **Registry Activity Analysis**

- **Total Events**: 8727  
  **Write Events**: 251  
  **Delete Events**: 24  

**Key Registry Modification**:
- `HKEY_CURRENT_USER\SOFTWARE\WinRAR\ArcHistory` was modified to include the path of the extracted .zip `(C:\Users\admin\AppData\Local\Temp\2ec35da14989692e77df25d56c7b1d43a3e93a72ec2fc7cce67b2fa448744752.zip)`.
  
Screenshot [here](https://ibb.co/JjKTRT8X)

**Interpretation**: While the modification of `ArcHistory` by WinRAR looks normal, it's important to analyze the registry activity along with other patterns.

Malware often manipulates the registry to ensure it remains active after system reboots or to alter system configurations for malicious purposes.

---

### 3. **File Activity Analysis**

**Suspicious Files Identified**:
- **MD5**: 1B109EFADE90ACE7D953507ADB1F1563  
- **SHA256**: 2EC35DA14989692E77DF25D56C7B1D43A3E93A72EC2FC7CCE67B2FA448744752  
  - **File Name**: `2ec35da14989692e77df25d56c7b1d43a3e93a72ec2fc7cce67b2fa448744752.xlsm`
    
Screenshot [here](https://ibb.co/SXF8NqtD)

**Dropped Files**:
- The malicious Excel document (`.xlsm`) was dropped in a temporary directory: `C:\Users\admin\AppData\Local\Temp\Rar$DIb2076.17793`. 
  This could indicate a common tactic for malware, as temporary folders can be used to hide malicious files before they are executed.

**Additional Suspicious File Access**:
- The analysis revealed attempts to access locations such as `\WebServiceCache`, `\TokenBroker\Cache`, and `\Recent\CustomDestinations`, areas where Windows stores temporary files and information.
 
These areas are often targeted by attackers as they might try to gather information about the user or the system from here, which could later lead to data harvesting or further exploitation.

Screenshot [here](https://ibb.co/chvjKGYP)
  
In such cases, it`s important to not just look where a file is dropped, but also what it does afterward, to fully understand its scope.

---

### 4. **Network Activity**

#### **HTTP(S) Requests**:
- **svchost.exe**: Made a web request to `http://ocsp.digicert.com`  
- **MoUsoCoreWorker.exe**: Request to `http://crl.microsoft.com`  
- **EXCEL.EXE**: Multiple web requests to `http://ocsp.digicert.com`
  
 While Any.Run flagged these websites as legitimate (certificate validation), I made a double check using VirusTotal, which confirmed their trusted status.

Screenshot [here](https://ibb.co/k2gG5Gww)

 From a threat analysis perspective, the presence of such requests suggests that the malware is trying to connect to a server (C2) to make sure it's functioning as intended.

#### **DNS Requests**:
- Main domains identified:
  - `settings-win.data.microsoft.com`
  - `crl.microsoft.com`
  - `google.com`
  - `ocsp.digicert.com`

Screenshot [here](https://ibb.co/93Np5d3y)

These requests confirm that, while they were legitimate, it's crucial to keep monitoring this activity for the malware analysis, as DNS is a critical component in network security monitoring and threat intelligence. 

---

### 5. **TCP/UDP Connections**:

We could see that most of the TCP/UDP connections are established to known, trusted addresses, primarily used for certificate validation (`crl.microsoft.com` and `ocsp.digicert.com`). 

The rest of them marked with "?" might require  to be carefully handled since they are not whitelisted and could represent potential anomalies. Screenshot [here](https://ibb.co/KHsk0pH))

Malware can use network connections to talk to its server, so it's important to properly examine all connections and verify through multiple sources. 

---

## Conclusion and Insights

Through this comprehensive analysis, I have effectively demonstrated my expertise in:

-  Sandboxing environments like Any.Run to analyze malware behavior in a controlled setting.
-  Registry Analysis:Understanding how malware tries to stay hidden by changing system settings.
-  Network Traffic Analysis: Meticulously examining network traffic including website connections, because malware can hide its communication even in normal-looking activity and can exfiltrate data.
- Threat Intelligence: Extracting key IOCs and behavioral patterns to better investigate vulnerabilities and inform about threat mitigation strategies.

---

## Actionable Security Recommendations
- using a network monitoring tool like Wireshark for a proactive analyze of DNS and HTTP(S) traffic patterns to detect unusual behavior (sign of malware communication).
- set up alerts for immediate notification on HKEY_CURRENT_USER\SOFTWARE\  modification through real time monitoring.
- integrate with SIEM the file hashes, registry changes etc., for an earlier and more efective detection of the attacks. 

---
