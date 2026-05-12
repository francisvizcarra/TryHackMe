# Tardigrade
Can you find all the basic persistence mechanisms in this Linux endpoint?

[TryHackMe Room](https://tryhackme.com/room/tardigrade})

## Introduction 
A server has been compromised, and the security team has decided to isolate the machine until it's been thoroughly cleaned up. Initial checks by the Incident Response team revealed that there are five different backdoors. It's your job to find and remediate them before giving the signal to bring the server back to production.

To start our investigation, we need to connect to the server. The IR team has provided the credentials for use below and noted that the user has root privileges to the server. I'll help guide you along at first, but as we progress through each step, I'm sure you'll feel more comfortable solving these on your own.

User: giorgio

Password: armani

---
---

## Answer the questions below
### 1. What is the server's OS version?

---

*Since we're in the giorgio account already, we might as well have a look around.*

### 2. What's the most interesting file you found in giorgio's home directory?

<details>
<summary>💡 Hint</summary>

```
Using the ls command on giorgio's home directory doesn't seem to return anything, so maybe we can find something interesting in the hidden files?
```

</details>

*In every investigation, it's important to keep a dirty wordlist to keep track of all your findings, no matter how small. It's also a way to prevent going back in circles and starting from scratch again. As such, now's a good time to create one and put the previous answer as an entry so we can go back to it later.*

### 3. Another file that can be found in every user's home directory is the .bashrc file. Can you check if you can find something interesting in giorgio's .bashrc?

<details>
<summary>💡 Hint</summary>

```
alias is a command that allows a string to be interpreted using a shorter, usually easier-to-remember "alias" for the string. Maybe there's a suspicious usage of alias somewhere?
```

</details>

*It seems we've covered the usual bases in giorgio's home directory, so it's time to check the scheduled tasks that he owns.*

### 4. Did you find anything interesting about scheduled tasks?

<details>
<summary>💡 Hint</summary>

```
cron is a great way to automate recurring tasks. Maybe there's a suspicious usage of cron?
```

</details>

---

*In the previous task, the concept of a dirty wordlist was introduced. In this task, we will discuss it in more detail.*

*A dirty wordlist is essentially raw documentation of the investigation from the investigator's perspective. It may contain everything that would help lead the investigation forward, from actual IOCs to random notes. Keeping a dirty wordlist assures the investigator that a specific IOC has already been recorded, helping keep the investigation on track and preventing getting stuck in a closed loop of used leads.* 

*It also helps the investigator remember the mindset that they had during the course of the investigation. The importance of taking note of one's mindset during different points of an investigation is usually given less importance in favour of focusing on the more exciting atomic indicators; however, recording it provides further context on why a specific bit is recorded in the first place. This is how pivot points are decided and further leads, born and pursued.*

*The advantages of a dirty wordlist don't end here. A quick way to formally document findings at the end of the investigation is to clean them up. It is recommended to put in every sort of detail that may help during the course of the investigation. So, in the end, it would be easy to remove all the unneeded details and false leads, enrich actual IOCs, and establish points of emphasis. The flag for this task is: THM{d1rty_w0rdl1st}*

*This section is a bonus discussion on the importance of a dirty wordlist. Accept the extra point and happy hunting!*

### 5. What is the flag?

---

*Normal user accounts aren't the only place to leave persistence mechanisms. As such, we will then go ahead and investigate the root account.*

*A few moments after logging on to the root account, you find an error message in your terminal.*

### 6. What does it say?

<details>
<summary>💡 Hint</summary>

```
Come on, do you really need a hint?
```

</details>

*After moving forward with the error message, a suspicious command appears in the terminal as part of the error message.*

### 7. What command was displayed?

*You might wonder, "how did that happen? I didn't even do anything? I just logged as root, and it happened."*

### 8. Can you find out how the suspicious command has been implemented?

<details>
<summary>💡 Hint</summary>
  
```
This file is essentially a file that executes whenever a user logs on, but more importantly, it executes whenever bash is started.
```

</details>

---

*After checking the giorgio and the root accounts, it's essentially a free-for-all from here on, as finding more suspicious items depends on how well you know what's "normal" in the system.*

*There's one more persistence mechanism in the system.*

*A good way to systematically dissect the system is to look for "usuals" and "unusuals". For example, you can check for commonly abused or unusual files and directories.*

*This specific persistence mechanism is directly tied to something (or someone?) already present in fresh Linux installs and may be abused and/or manipulated to fit an adversary's goals. What's its name?*

### 9. What is the last persistence mechanism?

<details>
<summary>💡 Hint</summary>
  
```
It's a usual user with an unusual characteristic.
```

</details>

---

*Now that you've found the final persistence mechanism, it's time to clean up. The persistence mechanisms tackled in this room are common and straightforward; as such, the process of eradicating them is simple.*

*The first four persistence mechanisms can be remediated by simply removing the mechanism (e.g. delete the file, remove the commands). The last one, however, involves bringing back the "unusuals" to their "usual" state, which is a bit more complex as you intend for that particular user, file or process to function as before.*

*Finally, as you've already found the final persistence mechanism, there's value in going all the way through to the end.*

*The adversary left a golden nugget of "advise" somewhere.*

### 10. What is the nugget?

<details>
<summary>💡 Hint</summary>
  
```
These hackers seem to like playing "hide the nugget"... Make sure to double check your working directory!
```

</details>

---
---
