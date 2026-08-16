# Email Structure & Headers Analysis

Understanding email architecture is fundamental for identifying phishing attempts and conducting forensic analysis. This document breaks down the key headers a SOC analyst inspects during an email-based incident investigation, and the methodology used to move from "this looks suspicious" to "this is confirmed phishing."

---

## 🔑 Key Headers for SOC Analysts

### 1. From Address
- **Display Name** vs **Actual Email Address** — these are two separate fields, and attackers exploit the gap between them.
- 🚩 **Red Flag:** `"Apple Support" <noreply@suspicious-domain.xyz>` — the display name impersonates a trusted brand while the domain has no relationship to it.

### 2. Received Headers
- Show the complete path an email took from sender to recipient, hop by hop across mail servers.
- Read **bottom to top** (oldest → newest) — the bottom entry is closest to the original sender.
- Used to trace the originating server and detect spoofed or relayed paths.

### 3. X-Originating-IP
- The sender's original IP address, when present.
- Critical for attribution — pivoting to WHOIS, geolocation, and threat-intel lookups.
- Example: `X-Originating-IP: [103.234.236.83]`

### 4. Authentication Results

| Header | Purpose |
|--------|---------|
| **SPF** | Verifies the sending IP is authorized to send mail for that domain |
| **DKIM** | Cryptographic signature validating the message wasn't altered in transit |
| **DMARC** | Policy telling receiving servers how to handle SPF/DKIM failures |

### 5. To / BCC Fields
- ⚠️ **Critical Red Flag:** Personal notifications (billing, security alerts, password resets) sent via **BCC**.
- Legitimate companies address individual communications directly in the **To:** field. Mass-BCC on a "personal" alert is a strong phishing indicator.

---

## 🧭 Process Workflow — Investigation Methodology

A repeatable sequence, not a random checklist — each step narrows the case and feeds the next:

```
1. Display Name vs Domain Match
      ↓
2. SPF / DKIM / DMARC Verification
      ↓
3. X-Originating-IP Attribution
      ↓
4. Received Chain Reconstruction
      ↓
5. To / BCC Field Inspection
      ↓
   Verdict: Legitimate / Suspicious / Confirmed Phishing
```

| Step | Analyst Action | What It Tells You |
|------|-----------------|--------------------|
| 1 | Compare the display name against the actual sending domain | Brand impersonation attempt |
| 2 | Check SPF/DKIM/DMARC pass or fail | Whether the sender is authorized — but **not** whether they're trustworthy |
| 3 | Extract and pivot on the originating IP | Geographic and infrastructure attribution |
| 4 | Walk the Received chain bottom-to-top | Whether the path is consistent or shows spoofing/relay abuse |
| 5 | Check who the mail was actually addressed to | Mass-BCC campaigns disguised as personal alerts |

This workflow matters more than any single header: a phishing email can pass SPF/DKIM and still be malicious, so the verdict comes from correlating **all five** checks, not stopping at the first green light.

---

## 📌 Key Takeaways

- ✅ **Always inspect the actual email address**, not just the display name.
- ✅ **BCC in personal notifications = Phishing** indicator.
- ✅ **SPF/DKIM Pass ≠ Legitimate** — attackers can configure authentication correctly on domains they own.
- ✅ **Geographic inconsistencies** (e.g. German domain + Chinese-language content + Indian physical address) = strong Phishing signal.
- ✅ A verdict is built by **correlating headers**, not reading one in isolation.

---

**Next:** [Phishing Techniques](./phishing-techniques.md)
