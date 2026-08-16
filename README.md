# 🛡️ Phishing Analysis & Detection

> A practical documentation of phishing analysis techniques, tools, and real-world case studies for SOC Analyst roles.

## 👨‍ About This Repository
This repository documents my journey and hands-on practice in analyzing phishing emails. It covers the fundamentals of email structure, advanced detection techniques, and the tools used to safely investigate malicious attachments and URLs without executing them.

## 🎯 Skills & Concepts
- **Email Forensics:** Analyzing Email Headers (Received, X-Originating-IP, SPF/DKIM).
- **Threat Detection:** Identifying Spoofing, BCC abuse, Brand Impersonation, and Social Engineering.
- **Safe Analysis:** Static analysis of attachments (Base64 decoding, Strings extraction) using CyberChef.
- **URL Analysis:** Unshortening links, Defanging URLs, and analyzing redirection chains.
- **Incident Response:** Understanding the SOC workflow (Triage, Containment, Escalation).

## 🛠️ Tools & Technologies
- **Analysis:** CyberChef, Thunderbird, Text Editors (Nano/Gedit).
- **Threat Intelligence:** VirusTotal, urlscan.io, CheckPhish, WhereGoes.
- **Sandboxing:** ANY.RUN, Hybrid Analysis (Conceptual understanding).
- **OS:** Linux (Ubuntu/Kali), Windows.

## 📂 Repository Structure
- **`Email Structure & Headers Analysis.md`**: Core concepts of email architecture, headers (From, To, BCC, X-Originating-IP, SPF/DKIM), and red flags.
- **`phishing-techniques.md`**: Common attacker tactics (Brand Impersonation, Spoofing, Urgency, Link Manipulation, BCC Abuse, Inconsistencies).
- **`examples.md`**: Real-world case studies (Netflix, Apple, DHL phishing campaigns) with analyst thought process.
- **`tools.md`**: Safe analysis workflow using CyberChef, VirusTotal, urlscan.io, CheckPhish, and Sandboxes.
- **`writeups/`**: TryHackMe room walkthroughs and solutions.


---
*Built for learning, documentation, and SOC Analyst portfolio building.*
