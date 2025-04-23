---
author: Sonam Tenzin
pubDatetime: 2025-04-23T20:15:00+06:00
modDatetime: 2025-04-23T20:15:00+06:00
title: Domain Information
featured: false
draft: false
tags:
  - enumeration
  - osint
  - passive-recon
description: Domain-level enumeration techniques including SSL certificate inspection, DNS record analysis, and passive infrastructure discovery.
---

# Domain Information

Domain information is a core component of any penetration test. It goes beyond subdomains—focusing on the company’s entire online presence. The purpose is to understand the company’s services, technologies, and infrastructure, often using **passive OSINT methods** that do not expose the tester.

## Goals:
- Understand services offered
- Infer underlying infrastructure
- Gather passive intel before active scans

---

## Initial Step: Analyze the Company Website
- Review text and services described.
- Infer technologies based on service types (e.g., app development, hosting, IoT).

> Enumeration Principles: Combine what we **see** and what we **don't**.

---

## Certificate Transparency (crt.sh)
- SSL certificates often reveal multiple subdomains.
- Use `crt.sh` or the command:

```bash
curl -s "https://crt.sh/?q=inlanefreight.com&output=json" | jq .
```

- Filter subdomains:
```bash
curl -s "https://crt.sh/?q=inlanefreight.com&output=json" | jq . | grep name | cut -d'"' -f4
```

---

## Identify Company-Hosted Servers
```bash
for i in $(cat subdomainlist); do
  host $i | grep "has address" | grep inlanefreight
done
```

Example:
```
blog.inlanefreight.com      10.129.24.93
matomo.inlanefreight.com    10.129.127.22
```

---

## Scan via Shodan
```bash
for i in $(cat ip-addresses.txt); do
  shodan host $i
done
```

Yields:
- Port info
- Server types (e.g., nginx, Apache)
- SSL versions
- City/Country of hosting

---

## DNS Records (via dig)
```bash
dig any inlanefreight.com
```

- **A records**: Point to IPs
- **MX records**: Mail server (e.g., Google)
- **NS records**: Name servers
- **TXT records**: Verifications, SPF, DKIM

---

## Extracted Insights from TXT Records
```
MS=ms92346782372
atlassian-domain-verification=...
google-site-verification=...
logmein-verification-code=...
v=spf1 include:mailgun.org include:_spf.google.com include:spf.protection.outlook...
```

These reveal:
- **Third-party tools in use**:
  - **Atlassian** (e.g., Jira/Confluence)
  - **Gmail** (cloud email)
  - **LogMeIn** (remote access)
  - **Mailgun** (email API)
  - **Outlook/Office 365**
  - **INWX** (domain registrar)

---

## Conclusion
- Passive domain enumeration provides critical insights without alerting the target.
- Enables smarter, more targeted active testing.
- Bridges into deeper OSINT or infrastructure-focused enumeration.
