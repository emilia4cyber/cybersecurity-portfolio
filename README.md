This report detects the Credential Dumping (T1003) technique using Windows Event Logs and Command Prompt. 
I`ve focused here on detecting suspicious activities through two key Event IDs:
a.4624 (Logon): indicating successful logon attempts.
b.4672 (Special Logon): indicating privileged account logons.

Short intro:
-Event ID 4624: indicates unusual times or sources from where the logs are generated.
-Event ID 4672: shows logons for accounts with administrator rights.

Mitigation techniques:
- MFA for privileged accounts.
- Regularly monitor logon events for suspicious behavior.
- Implement least privilege for all users.
