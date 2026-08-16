# Common Phishing Techniques

Attackers use a combination of psychological manipulation and technical tricks to bypass security controls and deceive victims.

## 🎭 1. Brand Impersonation
- **Concept:** Mimicking trusted entities (e.g., Netflix, Apple, DHL, Microsoft).
- **Indicators:** Use of official logos, HTML templates, and familiar language.
- **Detection:** Verify the actual sender domain, not just the visual design.

## 🎭 2. Display Name Spoofing
- **Concept:** Setting the "From" name to look legitimate while using a malicious email address.
- **Example:** `"Microsoft Support" <alert@random-xyz.com>`
- **Detection:** Always expand the sender details to reveal the actual email address.

## ⏱️ 3. Artificial Urgency
- **Concept:** Creating a false sense of panic to force quick, unthinking action.
- **Examples:** "Your account will be suspended in 24 hours", "Unauthorized purchase detected".
- **Detection:** Legitimate organizations rarely demand immediate action via email without prior notice.

## 🔗 4. Link Manipulation & Redirection Chains
- **Concept:** Hiding the final malicious destination behind multiple redirects or URL shorteners (e.g., bit.ly).
- **Example:** `http://trusted-lookalike.com/redirect?url=malicious-site.xyz`
- **Detection:** Use tools like **WhereGoes**, **urlscan.io**, or **CheckPhish** to trace the final destination without clicking. Always **defang** URLs in reports (e.g., `hxxp://malicious[.]xyz`).

## 📎 5. Malicious Attachments
- **Concept:** Bypassing email filters by embedding threats in files rather than direct links.
- **Common Formats:** 
  - `.zip` / `.rar` (Password-protected to evade scanning)
  - `.docm` / `.dot` (Word documents with malicious Macros)
  - `.xlsx` (Excel files with hidden links or Macros)
  - `.pdf` (Containing embedded malicious links or JavaScript)
- **Detection:** Analyze file hashes (SHA256) on **VirusTotal** or detonate in a **Sandbox** (ANY.RUN, Hybrid Analysis). **Never open attachments on a host machine.**

## 📨 6. BCC (Blind Carbon Copy) Abuse
- **Concept:** Sending bulk phishing emails while hiding the recipient list to appear as a "personal" automated notification.
- **Detection:** Legitimate personal notifications (billing, password resets) are **never** sent via BCC. If your email is in the BCC field for an "urgent" matter, it is highly likely a phishing campaign.

## 🌍 7. Geographical & Linguistic Inconsistencies
- **Concept:** Attackers reuse phishing kits across different regions without proper localization.
- **Example:** An email from a German domain (`.de`), addressed to an Indian city, with content written in Mandarin.
- **Detection:** Cross-reference the sender's domain, the recipient's location, and the language used.

---

**Next:** [Real-World Examples](../examples/)
