# Shadow Trace
Analyse a suspicious file, uncover hidden clues, and trace the source of the infection.

[TryHackMe Room](https://tryhackme.com/room/shadowtrace)

## Introduction
It’s the middle of the night shift. You’re the only analyst in the SOC when a manager calls in urgently: a suspicious file was found on a user's machine and needs immediate review.

You open the file and start digging. Something doesn’t look normal for a company updater, and at the same time, the EDR throws a couple of alerts.

Your task: analyse the file, collect anything to identify it, gather any potential IOCs, correlate and analyse the alerts for potential malicious behaviour. It’s up to you to piece together what’s happening before it spreads further.

## Objectives
- Extract IOCs from suspicious binaries
- Correlate alerts with malicious activity
- Perform basic SOC triage actions

## Tools Used
- CyberChef
- dCode
- PEStudio

---
---

## Answer the questions below
### 1. What is the architecture of the binary file windows-update.exe?

### 2. What is the hash (sha-256) of the file windows-update.exe?

### 3. Identify the URL within the file to use it as an IOC

### 4. With the URL identified, can you spot a domain that can be used as an IOC?

### 5. Input the decoded flag from the suspicious domain

### 6. What library related to socket communication is loaded by the binary?

---

### 7. Can you identify the malicious URL from the trigger by the process powershell.exe?

### 8. Can you identify the malicious URL from the alert triggered by chrome.exe?

### 9. What's the name of the file saved in the alert triggered by chrome.exe?

---
---

## References
- https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=VkVoTmUzbHZkVjluTUhSZmMyOXRaVjlKVDBOelgyWnlhV1Z1WkgwPQ
- https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=YUhSMGNITTZMeTkwY25sb1lYUnRaUzVqYjIwdlpHVjJMMjFoYVc0dVpYaGw
- https://www.dcode.fr/cipher-identifier
- https://www.dcode.fr/ascii-code

