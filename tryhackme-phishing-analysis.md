# TryHackMe: Phishing Analysis Module

Completion of the Phishing Analysis learning path on TryHackMe, covering both theoretical fundamentals and practical application.

## 📚 Room 1: Phishing Analysis Fundamentals
**Status:** ✅ Completed  
**Focus:** Understanding email architecture and core detection concepts.

### Key Learnings:
- **Email Header Analysis:** How to read and interpret `Received`, `X-Originating-IP`, `Authentication-Results` (SPF/DKIM/DMARC).
- **Identifying Red Flags:** Display name mismatches, suspicious sender domains, missing authentication.
- **Safe Analysis Techniques:** Extracting email source code, identifying Base64 encoded content.
- **Understanding Phishing Anatomy:** From the initial email to the final payload or credential harvest.

### Practical Skills Gained:
- Viewing email source code in Thunderbird/Outlook
- Tracing email paths through Received headers
- Identifying spoofed sender addresses
- Recognizing failed or missing SPF/DKIM authentication

---

## 🔬 Room 2: Phishing Emails in Action
**Status:** ✅ Completed  
**Focus:** Applying detection techniques to real-world phishing samples.

### Case Studies Analyzed:

#### 1. **Netflix Billing Scam**
- **Technique:** PDF attachment with hidden malicious URL
- **Analysis:** Used CyberChef to decode Base64 and extract strings
- **Outcome:** Identified credential harvesting attempt via fake login portal

#### 2. **Apple Support BCC Campaign**
- **Technique:** Bulk phishing via BCC with blank body and `.dot` attachment
- **Red Flags:** 
  - Victim email in BCC field (not To)
  - Completely blank email body
  - Suspicious `.dot` file extension (Word Template)
- **Outcome:** Identified as bulk malware delivery campaign

#### 3. **DHL Express Shipping Notification**
- **Technique:** `.xlsx` attachment with embedded malicious link
- **Red Flags:**
  - Geographical inconsistency (German domain + Indian address + Chinese text)
  - Link attempting to download `regasms.exe`
- **Outcome:** Identified as executable payload delivery (potential ransomware/data theft)

### Tools Practiced:
- **CyberChef:** Base64 decoding, strings extraction, URL defanging
- **VirusTotal:** Hash-based reputation checking
- **urlscan.io / WhereGoes:** URL redirection chain analysis
- **Thunderbird:** Email source code inspection

---

## 🎯 Skills Demonstrated
✅ Email header forensics and authentication analysis  
✅ Static analysis of attachments without execution  
✅ URL tracing and redirection chain analysis  
✅ Identification of social engineering tactics (urgency, brand impersonation)  
✅ Safe analysis workflow in isolated environments  
✅ Recognition of geographical and linguistic inconsistencies  

---

**Next Challenge:** [Blue Team Labs Online](https://blueteamlabs.online/) | [LetsDefend](https://letsdefend.io/)
