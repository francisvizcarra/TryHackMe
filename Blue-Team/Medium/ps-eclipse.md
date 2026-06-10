# PS Eclipse
Use Splunk to investigate the ransomware activity.

[TryHackMe Room](https://tryhackme.com/room/posheclipse)

## Introduction
You are a SOC Analyst for an MSSP (Managed Security Service Provider) company called **TryNotHackMe**.

A customer sent an email asking for an analyst to investigate the events that occurred on Keegan's machine on **Monday, May 16th, 2022**. The client noted that **the machine** is operational, but some files have a weird file extension. The client is worried that there was a ransomware attempt on Keegan's device.

Your manager has tasked you to check the events in Splunk to determine what occurred in Keegan's device. 

Happy Hunting!

## Tools Used
- CyberChef
- Splunk
- VirusTotal

---
---

## Answer the questions below
### 1. A suspicious binary was downloaded to the endpoint. What was the name of the binary?

### 2. What is the address the binary was downloaded from? Add http:// to your answer & defang the URL.

<details>
<summary>💡 Hint</summary>

```
CyberChef can help with defanging the URL.
```

</details>

### 3. What Windows executable was used to download the suspicious binary? Enter full path.

### 4. What command was executed to configure the suspicious binary to run with elevated privileges?

<details>
<summary>💡 Hint</summary>

```
Event Code 12 will help here. Note that the attacker tried multiple attempts to configure this command correctly.
```

</details>

### 5. What permissions will the suspicious binary run as? What was the command to run the binary with elevated privileges? (Format: User + ; + CommandLine)

### 6. The suspicious binary connected to a remote server. What address did it connect to? Add http:// to your answer & defang the URL.

<details>
<summary>💡 Hint</summary>

```
CyberChef can help with defanging the URL.
```

</details>

### 7. A PowerShell script was downloaded to the same location as the suspicious binary. What was the name of the file?

### 8. The malicious script was flagged as malicious. What do you think was the actual name of the malicious script?

<details>
<summary>💡 Hint</summary>

```
Check VirusTotal for the hash of the PowerShell script.
```

</details>

### 9. A ransomware note was saved to disk, which can serve as an IOC. What is the full path to which the ransom note was saved?

### 10. The script saved an image file to disk to replace the user's desktop wallpaper, which can also serve as an IOC. What is the full path of the image?

---
---

## References
