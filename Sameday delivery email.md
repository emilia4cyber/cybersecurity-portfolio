# Phishing Simulation: SameDay Delivery Email  

## Overview
This project simulates a phishing email impersonating the courier company **SameDay**.

My goal is to demonstrate how attackers create deceptive emails to trick users into interacting with malicious content, such as links and attachments.

## Scenario case
The phishing email informs the recipient that his recent order is ready for delivery and **asks them to reconfirm their house number**. 

The email includes:
- a **malicious link** disguised as a tracking button
- a **`.docx` attachment** presented as legitimate only for customers details
- the hurry of the task to be completed **within 24 hours**, or risk cancellation
- several gramatical errors

---

## Email samples

### 1. Hover effect
Screenshot [here](https://ibb.co/v4msrrmP)!

When hovering over the red button **"Track Order"** , the link leads to a **spoofed domain** `sameday-delivery.com` – a fake version of the legitimate SameDay website.  
This fake website asks users to **enter Google account credentials** in order to get up to date information. (Simulation only – the fake website was never created)


---

### 2. Email preview
This is how the phishing email appears in the inbox. [screenshot](https://ibb.co/qYH1tLQw)!

---

### 3. The `.docx` file attachment
The email includes a `.docx` file asking the user to "confirm" their address. [screenshot](https://ibb.co/PsZ9Rg92)!

Besides that the attackers use generally zip and exe formats.

---

## Concerns to be aware of
- **Generic greeting**: No personalized name; they used "dear valuable customer"
- **Urgency**: “Act now”, “within 24 hours” , "immediate action"
- **Fake domain**: Hovering over the link reveals `sameday-delivery.com`, and not the legitimate SameDay URL
- **Suspicious attachment**: `.docx` file used for "legitimate" purposes
- **Grammatical mistakes** which make us think this is not a legitimate source :"re-confirm", "proces", "," instead of ".", etc [screenshot](https://ibb.co/qYVmqg17)!

---


## MITRE ATT&CK Mapping

| Technique | ID | Description |
|----------|----|-------------|
| [Phishing: Spearphishing Attachment](https://attack.mitre.org/techniques/T1566/001/) | T1566.001 | The attacker attached a  `.docx` file to seem legitimate and trick the user. |
| [User Execution: Malicious Link](https://attack.mitre.org/techniques/T1204/001/) | T1204.001 | This technique relies on the receiver to click on "track order" and land to the page destination. |
| [Initial Access](https://attack.mitre.org/tactics/TA0001/) | TA0001, namely T1566 | Gaining entry to a system through customer's action. |
| [Masquerading](https://attack.mitre.org/techniques/T1036/) |	T1036	|Te attacker made malicious files and links to appear legitimate.
| [Valid Accounts](https://attack.mitre.org/techniques/T1078/) | T1078 |	After stealing the user credentials, the attackers would further access services like Gmail or internal systems of companies. (privilege escalation)

---

## Limitations
Due to Gmail’s security restrictions, `.zip` files were not allowed in the simulation.

Therefore, I've used a **`.docx` file** as an attachment, which remains an available method for the attackers to deceive users.

---

## Recommendations for users
1 Always check email sender domains and verify legitimacy (I would recommend sites like VirusTotal to check it out).

2 Hover over links before clicking (if not sure about the destination, check number 1)

3 Avoid downloading files from unknown sources or emails you didn't expect.

4 Report everything suspicious to your security teams.

5 Don’t respond to threatening or urgent messages without verifying their source. 


Just THINK before. Ask yourself, what makes this true?
Think like hackers and invest in your security awareness.

---

