# Investigating with Splunk
Investigate anomalies using Splunk.

[TryHackMe Room](https://tryhackme.com/room/investigatingwithsplunk)

## Introduction
SOC Analyst **Johny** has observed some anomalous behaviours in the logs of a few windows machines. It looks like the adversary has access to some of these machines and successfully created some backdoor. His manager has asked him to pull those logs from suspected hosts and ingest them into Splunk for quick investigation. Our task as SOC Analyst is to examine the logs and identify the anomalies.

To learn more about Splunk and how to investigate the logs, look at the rooms [splunk101](https://tryhackme.com/room/splunk101) and [splunk201](https://tryhackme.com/room/splunk201).

All the required logs are ingested in the index **main**.

## Tools Used
- Splunk

---
---

## Answer the questions below
### 1. How many events were collected and Ingested in the index main?
The index has <mark>12256</mark> events.

### 2. On one of the infected hosts, the adversary was successful in creating a backdoor user. What is the new username?

```
Hint: Narrow down based on the Event ID that relates to the creation of a new user on the system.
```

By investigating the `Windows Event ID 4720`, the user creation event was identified. The backdoor user was <mark>A1berto</mark>.

### 3. On the same host, a registry key was also updated regarding the new backdoor user. What is the full path of that registry key?
By appending the `Sysmon Event ID 13` (registry modification), hostname `Micheal.Beaven`, and `A1berto` as a keyword in the query, the registry modification event were identified.

The full path of the registry key is <mark>`HKLM\SAM\SAM\Domains\Account\Users\Names\A1berto`</mark>.

### 4. Examine the logs and identify the user that the adversary was trying to impersonate.
The query uses the `stats` command with the `count` function to aggregate events by `TargetUserName`.

The adversary was impersonating the user <mark>Alberto</mark>.

### 5. What is the command used to add a backdoor user from a remote computer?
By pivoting to only this `index=main A1berto` query, the small number of events allowed singly investigation.

The command for adding the user was <mark>`C:\windows\System32\Wbem\WMIC.exe" /node:WORKSTATION6 process call create "net user /add A1berto paw0rd1`</mark>. 

It is important to note that `WMIC` is used for remote execution.

### 6. How many times was the login attempt from the backdoor user observed during the investigation?
By using the query `index=main EventID IN (4624, 4625) A1berto`, the result showed <mark>0</mark> trace of login attempts.

### 7. What is the name of the infected host on which suspicious Powershell commands were executed?

### 8. PowerShell logging is enabled on this device. How many events were logged for the malicious PowerShell execution?

### 9. An encoded Powershell script from the infected host initiated a web request. What is the full URL?

```
Hint: Defang the URL, CyberChef can help with this.
```

---
---
