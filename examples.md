# Real-World Phishing Case Studies

Practical analysis of real-world phishing campaigns, demonstrating the application of detection techniques and safe analysis workflows.

---

## 📺 Case Study 1: The "Netflix Billing" Campaign

### 🔍 **Initial Observations**
- **Subject:** Urgent billing notification with a same-day expiration date.
- **Sender:** Display name "Netllx billing" (notice the typo), mismatched domain.
- **Payload:** PDF attachment instead of a direct link.

### 🧠 **Analyst Thought Process**
1. **Urgency Check:** The "expires today" tactic is a classic social engineering trigger to bypass critical thinking.
2. **Attachment Analysis:** Instead of clicking, the PDF is extracted and analyzed statically.
3. **Static Analysis:** Using CyberChef to decode Base64 or extract strings reveals a hidden URL.
4. **URL Tracing:** The extracted URL is defanged (`hxxp://devret[.]xyz/...`) and checked via **urlscan.io** or **VirusTotal**.

### 🚩 **Verdict: Malicious (Credential Harvesting)**
The attacker used a trusted brand template to lure the victim into opening a PDF, which then redirected to a fake login portal designed to steal credentials.

---

## 🍎 Case Study 2: The "Apple Support" BCC Abuse

### 🔍 **Initial Observations**
- **Subject:** "Action Required: Unauthorized purchase detected".
- **Sender:** "Apple Support" `<support@suspicious-domain.com>`.
- **Recipient Field:** The victim's email is in the **BCC** field; the "To" field is empty or contains `undisclosed-recipients`.
- **Body:** Completely blank.
- **Payload:** A `.dot` (Microsoft Word Template) file.

### 🧠 **Analyst Thought Process**
1. **Header Red Flag:** Legitimate companies **never** send personal security alerts via BCC. This indicates a bulk, automated phishing blast.
2. **Blank Body:** Highly suspicious for a "billing" or "security" notification.
3. **File Extension Analysis:** `.dot` files are rarely used for receipts. They are often used to bypass basic email filters that block `.exe` or `.docm`, while still supporting malicious Macros.

### 🚩 **Verdict: Malicious (Malware Delivery)**
The use of BCC and a blank body confirms a bulk campaign. The `.dot` file is a vector to execute hidden macros or redirect the user to a malicious site upon interaction.

---

## 📦 Case Study 3: The "DHL Express" Inconsistency

### 🔍 **Initial Observations**
- **Subject:** Shipping notification for a pending package.
- **Sender:** "DHL Express" `<noreply@german-domain.de>`.
- **Payload:** `.xlsx` (Excel) attachment.
- **Content:** The invoice is addressed to a city in India, but the document text is written in Mandarin (Chinese).

### 🧠 **Analyst Thought Process**
1. **Geographical/Linguistic Check:** A German domain, an Indian address, and Chinese text is a massive inconsistency. This indicates the attacker is using a cheap, recycled "Phishing Kit" without proper localization.
2. **Attachment Behavior:** Opening the `.xlsx` reveals a single, prominent hyperlink.
3. **Payload Execution:** Clicking the link attempts to download and execute `regasms.exe`.

### 🚩 **Verdict: Malicious (Executable Payload Delivery)**
The geographical inconsistencies are a dead giveaway. The ultimate goal is to drop a `.exe` payload to establish persistence, exfiltrate data, or deploy ransomware.

---

## 🛡️ **Universal Safe Analysis Workflow Applied**
For all cases above, the following rules were strictly followed:
1. **Never** open attachments or click links on a host machine.
2. Extract file hashes (SHA256) and check **VirusTotal**.
3. Use **CyberChef** for static analysis of email source code.
4. Use **Sandboxing** (ANY.RUN, Hybrid Analysis) for dynamic behavior observation.
5. Always **Defang** URLs and IPs in documentation (e.g., `hxxp://malicious[.]com`).

---

**Next:** [Tools & Techniques](./tools/)
