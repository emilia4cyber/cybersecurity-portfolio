# Credential Dumping Detection - detailed report

In this report, I detect the technique T1003 called **Credential Dumping**.

According to attack.mitre.org, " Adversaries may attempt to dump credentials to obtain account login and credential material, normally in the form of a hash or a clear text password. Credentials can be obtained from OS caches, memory, or structures. Credentials can then be used to perform Lateral Movement and access restricted information."

I have used **Windows Event Logs** from Event Viewer (Windows logs -> Security) and could indicate 2 main **Event IDs**: **4624 (Logon)** and **4672 (Special Logon)**, that identified suspicious activities related to credential dumping.

### Event ID Analysis

1. **Event ID 4624: Successful Logon**
   - **Purpose**: This event is logged when a user successfully logs on to a system and it indicated unusual logon sessions in odd hours or from unexpected IP addresses for example.
     
    **How I generated it**:
     
     a) I had to activate Security Auditing from the Group Policy Editor, mainly the options "Audit Logon Events" and "Audit process tracking". (check screenshot - https://ibb.co/FqgnPkm8)
     
   b) In Command Prompt I ran the command ``` rundll32.exe C:\Windows\System32\shell32.dll,Control_RunDLL ``` (check screenshot- https://ibb.co/S7xLdz7n)
   
    c) Then I accessed Event Viewer and could observe the following details:
   - **Event Example**:
     ```
     
     Task Category: Logon
     Level:         Information
     Keywords:      Audit Success
     User:          N/A
     Description:   This event is generated when a logon session is created. It is generated on the computer that was accessed.
     The subject fields indicate the account on the local system which requested the logon. This is most commonly a service such as the Server service, or a local process such as Winlogon.exe or Services.exe.

     ```

   - **Screenshot with more details**: https://ibb.co/fYNfT06y
---
2. **Event ID 4672: Special Logon**
   - **Purpose**: This event lets you know whenever an account assigned any "administrator equivalent" user rights logs on and is often associated with the Event ID 4624.
     
   **How I generated it**: The same way like the Event ID 4624

   - **Event information according to Event Viewer**:
     ```
     
     Task Category: Special Logon
     Level:         Information
     Keywords:      Audit Success
     User:          N/A
  
     ```

   - **Screenshot with more details**: https://ibb.co/1GTRzfNg 
---

### Mitigation Strategies
To mitigate the risks associated with credential dumping, I would recommend the following:
- Applying Multi-Factor Authentication (MFA) for all privileged accounts.
- Regularly monitor and analyze logon events to detect suspicious activities.
- Applying least  privilege for all the users.
---
### Reference
```
https://attack.mitre.org/techniques/T1003/
```
---
### Summary
By examining **Event IDs 4624** and **4672**, I could get insights about **user logons** and **privileged access** , which could help me prevent credential dumping. 

