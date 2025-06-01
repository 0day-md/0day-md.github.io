---
title: Cheatsheet Bug Hunting
author: 0day
date: 2025-06-1 10:00:00 +0800
categories: [Cheatsheet]
tags: [Bug Hunter]
---

Whether you're diving into web apps, APIs, or binaries, bug hunting is a skill that blends creativity with technical know-how. Here's a curated cheatsheet to speed up your workflow and help you uncover vulnerabilities more efficiently.

---

## 🕵️ Reconnaissance

- **Subdomain Enumeration**
  - `subfinder -d example.com`
  - `amass enum -d example.com`
  - `assetfinder --subs-only example.com`
- **Google Dorking**
  - `site:example.com inurl:admin`
  - `site:example.com intitle:"index of"`

- **ASN and IP Ranges**
  - `whois example.com | grep -i "OrgName\|CIDR"`
  - `nmap -sn [ip range]`

---

## 🔎 Web Vulnerabilities

- **XSS (Cross-Site Scripting)**
  - Test payload: `<script>alert(1)</script>`
  - Check parameters and DOM sinks using `Dalfox`, `XSStrike`

- **SQLi**
  - `' OR '1'='1`
  - Tools: `sqlmap -u "http://example.com/page?id=1" --batch`

- **IDOR**
  - Change numeric or UUID identifiers
  - Use Burp Intruder to automate ID fuzzing

- **SSRF**
  - Payloads: `http://127.0.0.1:80`, `http://169.254.169.254/latest/meta-data/`
  - Monitor with `requestbin`, `Burp Collaborator`

---

## 🛠️ Tools Quick Access

- **Burp Suite** – Intercept traffic, scan for vulns, automate testing
- **FFUF** – Fast web fuzzing: `ffuf -u https://example.com/FUZZ -w wordlist.txt`
- **Nuclei** – Vulnerability templates: `nuclei -u https://example.com -t cves/`
- **httpx** – Probe for HTTP services: `httpx -l domains.txt -status -title -tech-detect`

---

## 📜 Reporting Tips

- Be clear and concise
- Include reproduction steps, impact analysis, and suggested fixes
- Use screenshots and annotated requests/responses
- Always follow the responsible disclosure policy

---

## 🧠 Pro Tips

- Stay curious – read writeups, CVEs, and bug bounty reports
- Automate repetitive tasks but always verify manually
- Think like an attacker *and* a developer

---

Happy Hunting! 🎯  
Stay safe, stay sharp.  
— **0day.md**

