# Snapped Phish-ing Line
Apply learned skills to probe malicious emails and URLs, exposing a vast phishing campaign.

[TryHackMe Room](https://tryhackme.com/room/snappedphishingline)

## Introduction
As a member of the IT department at SwiftSpend Financial, you are responsible for assisting employees with technical concerns. What initially appeared to be a routine day quickly escalated when multiple employees across different departments reported receiving a suspicious email. Several users noted unusual characteristics in the message, and unfortunately, some had already submitted their credentials and were no longer able to access their accounts. With the potential for a wider compromise, the incident has been escalated for investigation. Your task is to analyze the available evidence, determine the scope of the attack, and uncover how the adversary operated.

## Objectives
- Analyze the provided email samples to identify key artifacts
- Investigate phishing URLs to understand redirection
- Retrieve and examine the phishing kit used in the attack
- Use CTI tools to gather intelligence on the adversary
- Analyze the phishing kit to uncover additional indicators

## Tools Used
- CyberChef
- VirusTotal

### Answer the questions below
1. Begin reviewing the emails in the phish-emails folder on your desktop.
   Which individual received the email regarding a **Quote for Services Rendered**?
   - By accessing the phish-emails folder on the Desktop, the email about the Quote for Services Rendered can be investigated. The **To** field indicates that **William McClean** received the email.
     
   ![accessing the .eml file](images/phish-emails-folder.png)

   ![william mcclean](images/william-mcclean.png)
   
2. What email address was used by the adversary to send the phishing emails?
   -  In examining the **From** field, the adversary used **Accounts.Payable@groupmarketingonline.icu** to deliver the phishing emails.

   ![phishing email](images/quote-for-services-rendered-email.png)

3. Investigate the attachment in the email addressed to Zoe Duncan.
   What is the root domain of the redirection URL found within the file?
   - To further examine the attachment, it was opened using Firefox. The domain is **kennaroads.buzz**.
  
   ![zoe duncan email](images/zoe-duncan-email.png)

   ![redirection URL](images/kennaroads.buzz.png)

4. Open the attachment in your VM web browser.
   Which company is the login page impersonating?
   - It is impersonating **Microsoft**.

5. Let’s check if the attacker left any files exposed on the same website.
   Navigate to the **/data** directory.
   What is the name of the archive file?
   - By only navigating to this **http://kennaroads.buzz/data/** path, the **Update365.zip** can be located.
  
   ![Update365.zip](images/Update365.zip.png)

6. Download the phishing kit archive to your virtual environment.
   Using the **sha256sum** command, what is the **SHA256** hash of the file?
   - After downloading the phishing kit, the command **sha256sum Update365.zip** was ran to generate its hash, **ba3c15267393419eb08c7b2652b8b6b39b406ef300ae8a18fee4d16b19ac9686**.

   ![Update365.zip](images/sha256.png)
   
8. Investigate the file hash from the previous question using VirusTotal.
   Aside from **phishing**, what other threat category is assigned to the **ZIP** archive?
   - It is also listed as **Trojan**.

   ![trojan](images/virus-total-threat-categories.png)

9. Review the VirusTotal Details page for the phishing kit.
   How many files are contained within the archive?
   - In the Details tab, under Bundle Info, its metadata says that it contains **49** files.

   ![49 files](images/49-files.png)
   
13. Let’s see if the attacker has exposed any captured credentials.
    Navigate to the **/data/Update365/** directory and investigate the log file.
    What is the email address of the user who submitted their credentials more than once?

14. Extract the phishing kit archive and locate the **submit.php** file.
    What email address is used by the adversary to collect compromised credentials?

15. Return to the phishing URL and locate the **flag.txt** file.
    Using CyberChef to decode the flag, what is the secret value?
