# Risk Treatment Plan Example for Heroland

**According to the details displayed in the Risk_Assessment_Example.pdf**

## 1. Introduction

This Risk Treatment Plan provides actions to mitigate the identified information security risks, as part of an ISO 27001 Risk Management exercise.

## 2. Identified Risks and Treatment Actions

### A. Risk ID: Risk-001 - School Contact Database: Ransomware Attack
* **Risk Description:** Ransomware attack on the School Contact Database due to weak password policy or missing MFA.Contains contact information, school details, order history, contract terms, and pricing agreements for school customers.
* **Risk Level:** High (Risk Score: 15)
* **Risk Treatment Options Recommended:**
    * Avoidance: Not efficient, since the database is essential for business.
    * Transfer: Cyber insurance could transfer some financial risk.
    * Mitigation: Could be the primary approach to reduce likelihood and impact, by enforcing MFA, conducting regular security audits.
    * Acceptance: Acceptance not recommended due to high risk level and the impact having on business continuity.
* **Chosen Risk Treatment Action:** Risk mitigation
* **Actions for implementation:**
    * Enforcing Multi-Factor Authentication (MFA) for all database access.
    * Creating stronger password policies and regular password changes for database accounts.
    * Implement robust backup and recovery procedures for the database, including offsite backups.
    * Conduct regular vulnerability scanning and penetration testing of database systems.
* **Responsibility:** IT Manager 
* **Target Completion Date:** 1st August 2025.

### B. Risk ID: Risk-002 - Heroland Financial Records: Phishing Attack
* **Risk Description:** Phishing attack targeting Heroland Financial Records due to untrained staff, which could lead to data breach. Systems containing Heroland's financial information, like invoices, payment details, and financial reports.
* **Risk Level:** Medium (Risk Score: 8)
* **Risk Treatment Options Recommended:**
    * Avoidance: Not recommended because the email is essential for communication.
    * Transfer: Cyber insurance could help in covering some damaged caused by phishing attacks.
    * Mitigation: Could suit best, since we could implement security awareness training and improve the e-mail filtering.
    * Acceptance: Acceptance not recommended due to the impact which could lead to high damages.
* **Chosen Risk Treatment Action:** Risk mitigation
* **Actions for implementation:**
    * Implementing mandatory annual security awareness training for all staff, focusing on phishing identification and prevention.
    * Implementing technical controls such as email filtering.
    * Establishing clear procedures for reporting suspicious emails and potential security incidents.
* **Responsibility:** Finance Manager
* **Target Completion Date:** 30th December 2025

### C. Risk ID: Risk-003 - Heroland Public Website DDoS Attack
* **Risk Description:** DDoS could attack the Heroland Public Website,- which could cause unavailability and revenue loss. The website promotes Heroland’s services, allowing schools to order online.
* **Risk Level:** Medium (Risk Score: 9)
* **Risk Treatment Options Recommended:**
    * Avoidance: Not a real option, as the website is essential for business continuity.
    * Transfer: Using a cloud-based hosting provider with built-in DDoS protection (like Cloudflare) can transfer some of the risk.
    * Mitigation: Could be a solution if we choose to implement better Web Application Firewalls, to monitor ghe traffic etc.
    * Acceptance: Not recommended or is discutable after the mitigation methods have taken place.
* **Chosen Risk Treatment Action:** Risk mitigation and risk transfer
* **Actions for implementation:**
    * Implement a WAF with capabilities against DDoS attacks, in order to block malicious traffic.
    * Using a Cloud-Based Service with DDoS protection.
    * Establish a DDoS incident response plan to handle attacks effectively. (This includes to establish traffic rerouting strategies to minimize downtime).
* **Responsibility:** Marketing Manager
* **Target Completion Date:** 15th February 2026

### D. Risk ID: Risk-004 - Employee Laptop: Loss or Theft
* **Risk Description:** Loss or theft of the employee laptops could cause data breach due to missing of full disk encryption.Laptops used by Heroland employees for daily work contain customer data, documents with sensitive data, etc.
* **Risk Level:** Low (Risk Score: 6)
* **Risk Treatment Options Recommended:**
    * Avoidance: Not applicable, as employees require laptops for work, they could start rather saving the data on secure cloud storages.
    * Transfer: Cyber insurance can help to cover some costs, yet might not fully mitigate data breach risks.
    * Mitigation: Is the primary approach to prevent unauthorized data access.
    * Acceptance: Not recommended or is discutable after the mitigation methods have taken place.
* **Chosen Risk Treatment Action:** Risk mitigation
* **Actions for implementation:**
    * Implementing full disk encryption (like BitLocker for Windows) on all company-issued laptops and devices.
    * Enforcing a policy requiring stronger authentication.
    * Enabling remote wipe capability for lost or stolen laptops.
* **Responsibility:** HR Manager
* **Target Completion Date:** 20th December 2025

### E. Risk ID: Risk-005 - Acer Supplier Account: Spyware 
* **Risk Description:** Spyware tool compromising Acer Supplier Account Information due to weak login credentials or vulnerable browser plugins, which could lead to unauthorized access and supply chain disruption. Includes login credentials for Acer supplier portal, pricing lists and communication records with Acer.
* **Risk Level:** Medium (Risk Score: 12)
* **Risk Treatment Options Recommended:**
    * Avoidance: Not recommended, as supplier account access is essential.
    * Transfer: A cyber insurance may cover but not entirely some financial losses during the account compromise.
    * Mitigation: Could be the best option, since it's crucial to  protect supplier account access in order to prevent data compromise.
    * Acceptance: Not recommended due to the Medium risk level and potential business impact.
* **Chosen Risk Treatment Action:** Risk mitigation
* **Actions for implementation:**
    * Implementing (MFA) for all Acer supplier account logins.
    * Require strong and unique passwords for supplier accounts.
    * Automate scans on employee computers for spyware and malware using updated antivirus software.
    * Restrict unauthorized plugins.
* **Responsibility:** Supply Chain Manager 
* **Target Completion Date:** 5th May 2025

## 3. Risk Treatment Plan Review and Monitoring

This Risk Treatment Plan will be reviewed and updated on each quarter by the Security Team, under the coordination of the IT Manager.

This will help track the progress of implementation, evaluate how efficient each control is, and address any new changes in risks.

