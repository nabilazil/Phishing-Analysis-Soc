# SOC Analysis Tools & Safe Workflow

A practical guide to the tools and methodologies used for safe and effective phishing analysis without executing malicious payloads.

## 🛠️ 1. Static Analysis: CyberChef
**Purpose:** Decoding and extracting hidden data from email source code or attachments without execution.
- **Key Recipes Used:**
  - `From Base64`: Decodes Base64 encoded attachments or email bodies.
  - `Strings`: Extracts readable text (like hidden URLs or domains) from binary files.
  - `Defang URLs`: Automatically converts `http://evil.com` to `hxxp://evil[.]com` for safe reporting.
- **Rule:** Always analyze in the browser or an isolated VM. Never download and open the decoded payload locally.

## 🔍 2. URL & Domain Analysis
**Purpose:** Tracing the final destination of shortened or obfuscated links safely.
- **WhereGoes / Unshorten.it:** Traces the full redirection chain (e.g., `bit.ly` ➔ `tracking.com` ➔ `malicious.xyz`) without visiting the site.
- **urlscan.io:** Provides a safe screenshot of the landing page and extracts all associated IPs, domains, and JavaScript.
- **CheckPhish:** Specialized in detecting brand impersonation and fake login portals.
- **Rule:** Always **Defang** URLs in notes and reports (e.g., `hxxps://phishing-site[.]com/login`).

## 🧬 3. Hash & Sandbox Analysis
**Purpose:** Determining the maliciousness of an attachment through reputation and dynamic behavior.
- **VirusTotal (First Step):** 
  - Search by **SHA256/MD5 Hash** (extracted via terminal or CyberChef).
  - Provides a quick reputation check across 70+ antivirus engines.
- **ANY.RUN / Hybrid Analysis (Second Step):**
  - Used if the hash is unknown (Zero-Day) or requires behavioral analysis.
  - Detonates the file in an isolated, interactive cloud VM.
  - **What to look for:** Network connections to suspicious IPs, spawned processes (e.g., `winword.exe` spawning `powershell.exe`), and registry modifications.
- **Rule:** **NEVER** upload files containing real company data, PII, or credentials to public sandboxes.

## 🔄 The Golden Rule of Phishing Analysis
> **"Analyze without Executing."** 
> A SOC Analyst's primary goal during triage is to understand the threat and contain it, not to become the next victim. All analysis must be performed in isolated environments (VMs, Sandboxes, or Web-based tools).

---

**Next:** [TryHackMe Write-ups](./tryhackme-phishing-analysis.md/)
