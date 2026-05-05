# Investigating with Splunk
Investigate anomalies using Splunk.

[TryHackMe Room](https://tryhackme.com/room/investigatingwithsplunk)

## Introduction
SOC Analyst **Johny** has observed some anomalous behaviours in the logs of a few windows machines. It looks like the adversary has access to some of these machines and successfully created some backdoor. His manager has asked him to pull those logs from suspected hosts and ingest them into Splunk for quick investigation. Our task as SOC Analyst is to examine the logs and identify the anomalies.

## Tools Used
- Splunk

---
---

## Answer the questions below
### 1. How many events were collected and Ingested in the index main?

### 2. On one of the infected hosts, the adversary was successful in creating a backdoor user. What is the new username?

```
Hint: Narrow down based on the Event ID that relates to the creation of a new user on the system.
```

### 3. On the same host, a registry key was also updated regarding the new backdoor user. What is the full path of that registry key?

### 4. Examine the logs and identify the user that the adversary was trying to impersonate.

### 5. What is the command used to add a backdoor user from a remote computer?

### 6. How many times was the login attempt from the backdoor user observed during the investigation?

### 7. What is the name of the infected host on which suspicious Powershell commands were executed?

### 8. PowerShell logging is enabled on this device. How many events were logged for the malicious PowerShell execution?

### 9. An encoded Powershell script from the infected host initiated a web request. What is the full URL?

```
Hint: Defang the URL, CyberChef can help with this.
```

