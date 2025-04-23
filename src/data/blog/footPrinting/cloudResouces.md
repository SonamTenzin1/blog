---
author: Sonam Tenzin
pubDatetime: 2025-04-23T20:20:00+06:00
modDatetime: 2025-04-23T20:20:00+06:00
title: Cloud Resources
featured: false
draft: false
tags:
  - cloud
  - osint
  - aws
  - azure
  - gcp
description: Identifying and analyzing misconfigured cloud resources and storage using passive reconnaissance methods like Google Dorks, GrayHatWarfare, and DNS records.
---

# Cloud Resources

Cloud platforms such as **AWS**, **GCP**, and **Azure** are now core infrastructure for many businesses. They offer flexibility, centralized management, and remote access. However, despite strong security at the provider level, **misconfigurations by administrators** can expose cloud resources publicly.

---

## Common Vulnerabilities in Cloud

- **Unauthenticated access** to:
  - S3 Buckets (AWS)
  - Azure Blobs
  - GCP Storage Buckets

---

## Cloud Detection via DNS

From subdomain scans:

```bash
for i in $(cat subdomainlist); do
  host $i | grep "has address" | grep inlanefreight
done
```

Example result:
```
s3-website-us-west-2.amazonaws.com 10.129.95.250
```

Such addresses suggest exposed **cloud storage endpoints**. These may be used internally but are sometimes publicly accessible.

---

## Passive Discovery Using Google Dorks

Use `inurl:` and `intext:` with a company name:
```
inurl:s3.amazonaws.com filetype:pdf
intext:azure blob storage
```

These reveal:
- PDFs
- Docs
- Source code links
- Cloud-hosted media files

> Often, files or scripts hosted on S3/Azure/GCP are referenced in public **website source code**.

---

## Tools for Enumeration

### 1. **domain.glass**
- Shows domains and CDN info
- Example: Detecting Cloudflare
- Can map **infrastructure** and security controls (useful for gateway layer analysis)

### 2. **GrayHatWarfare**
- Searches public **AWS, GCP, and Azure** buckets
- Filters by **file types**
- Ideal for finding leaks and exposed company data

---

## Naming Convention Tip

Companies often use **abbreviations** or acronyms in their cloud infrastructure naming. Try variations to increase discovery chance.

---

## Real Threat: Leaked SSH Keys

Due to pressure or poor hygiene, **private SSH keys** sometimes get uploaded accidentally:

- Commonly found via:
  - Public repos
  - Exposed buckets
  - Search engines

Once found, they can grant:
- **Shell access**
- **Lateral movement**
- **Persistence**

---

## Summary

- Cloud misconfigurations are a major risk area.
- Passive enumeration methods (like Google and GrayHatWarfare) are powerful in identifying exposed storage.
- DNS and source code often leak endpoints.
- Stay alert for sensitive files like **SSH private keys** or configuration files.
- Use tools like **domain.glass** and **GrayHatWarfare** for deeper insights.
- Always follow up with active testing to confirm findings and assess risk.






























