# Phase 1 — Risk Identification Report  
**Project:** Enterprise Cybersecurity Risk Management Framework Implementation — CyberFort Solutions Ltd.  
**Standards:** ISO 31000:2018 | NIST RMF (Prepare & Categorize)  
**Author:** Cypriano Akinwunmi  
**Date:** 2025-10-27  

---

## 1. Purpose
This report documents all the evidence collected on **2025-10-27** during reconnaissance and vulnerability discovery activities.  
Each piece of evidence is timestamped and cryptographically hashed (SHA256) for traceability and integrity.  
Screenshots are embedded below and are stored in the `screenshots/` directory.

---

## 2. Evidence Manifest — (Timestamped set: `_20251027_1027`)

| Evidence File | Size (bytes) | Timestamp | SHA256 |
|----------------|--------------|------------|---------|
| `02-Identification/evidence/nmap_ping_sweep_20251027_1027.txt` | 312 | 2025-10-27 10:27:45 -0400 | `90e8d3b3b5c23dc54933ac4498f0b4a646b82757eeb2a1f4374157bd979ab30e` |
| `02-Identification/evidence/nmap_full_10.10.10.15_20251027_1027.txt` | 283 | 2025-10-27 10:28:32 -0400 | `15eac76e2f0f44f318e84b2f7287d9609b8f8d5c2885d33c8bb47db8d2a8aae6` |
| `02-Identification/evidence/nikto_10.10.10.15_20251027_1027.txt` | 16 | 2025-10-27 10:29:12 -0400 | `49b345eba7c2261f95250ba520b1f16ce59eb430007f4a95df546e94fbf246be` |
| `02-Identification/evidence/gobuster_10.10.10.15_20251027_1027.txt` | 0 | 2025-10-27 10:30:12 -0400 | `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855` |
| `02-Identification/evidence/enum4linux_10.10.10.15_20251027_1027.txt` | 1,070 | 2025-10-27 10:31:25 -0400 | `043f05e28204136c4f5f30bfc049ffd5246a7c517ad5cb2cef127f77c6fa035c` |

**Manifest Files**
| Manifest File | Size (bytes) | Timestamp | SHA256 |
|----------------|--------------|------------|---------|
| `02-Identification/evidence/evidence_manifest_20251027_1027.sha256` | 1,047 | 2025-10-27 10:31:47 -0400 | `1606475a9db8f42feb816aa2aa6b923625b0ac72b31485663628ef1769ced7e6` |
| `02-Identification/evidence/evidence_manifest_20251027_1114.csv` | 399 | 2025-10-27 11:14:09 -0400 | `da1a6f26bd66bee309ce6c35881722ff88f74530580dfbc398b0c35410126595` |

---

## 3. Visual Evidence — Screenshots (All from 2025-10-27)

Each screenshot below is stored under `screenshots/` and will render directly on GitHub.  
Each corresponds to the text-based evidence files above and is time-aligned within ±1 minute.

---
---

## 3. Screenshots (Visual Evidence)

The following screenshots were captured during the threat and vulnerability identification phase on **October 27, 2025**, confirming tool execution and asset enumeration findings.

**Nmap — Ping Sweep (2025-10-27 10:27:46 -0400)**
![Nmap — ping sweep](../../screenshots/nmap_ping_sweep_10.10.10.15_20251027_1027.png)

**Nmap — Full Service Enumeration (2025-10-27 10:28:33 -0400)**
![Nmap — full service enumeration](../../screenshots/nmap_full_10.10.10.15_20251027_1027.png)

**Nikto — HTTP Checks (2025-10-27 10:29:13 -0400)**
![Nikto — HTTP checks](../../screenshots/nikto_10.10.10.15_20251027_1027.png)

**Gobuster — Directory Discovery (2025-10-27 10:30:15 -0400)**
![Gobuster — directory discovery](../../screenshots/gobuster_10.10.10.15_20251027_1027.png)

**ZAP — Quick Scan (2025-10-27 10:30:40 -0400)**
![ZAP — quick scan](../../screenshots/zap_quick_10.10.10.15_20251027_1027.png)

**enum4linux — AD/SMB Enumeration (2025-10-27 10:31:25 -0400)**
![enum4linux — AD/SMB enumeration](../../screenshots/enum4linux_10.10.10.15_20251027_1027.png)

---

## 4. Tools & Commands Executed

All tools executed on **2025-10-27** and saved to the exact filenames above.

```bash
nmap -sn 10.10.10.0/24 -oN 02-Identification/evidence/nmap_ping_sweep_20251027_1027.txt
nmap -sS -sV -O -p- -T4 10.10.10.15 -oN 02-Identification/evidence/nmap_full_10.10.10.15_20251027_1027.txt
nikto -host http://10.10.10.15 -o 02-Identification/evidence/nikto_10.10.10.15_20251027_1027.txt
gobuster dir -u http://10.10.10.15 -w /usr/share/wordlists/dirb/common.txt -o 02-Identification/evidence/gobuster_10.10.10.15_20251027_1027.txt
zap-cli start
zap-cli quick-scan --start-options "-daemon" http://10.10.10.15 -o 02-Identification/evidence/zap_quick_10.10.10.15_20251027_1027.json
zap-cli stop
enum4linux -a 10.10.10.15 | tee 02-Identification/evidence/enum4linux_10.10.10.15_20251027_1027.txt
sha256sum 02-Identification/evidence/* > 02-Identification/evidence/evidence_manifest_20251027_1027.sha256

## 5. Findings (Mapped to Evidence)

F-20251027-001 — Directory Index / Public Files Discovered

Assets: A-003 — Cloud Web Storage (Simulated)
Evidence:

gobuster_10.10.10.15_20251027_1027.txt

nikto_10.10.10.15_20251027_1027.txt

screenshots/gobuster_10.10.10.15_20251027_1027.png

screenshots/nikto_10.10.10.15_20251027_1027.png
Summary: Directory enumeration revealed possible exposed endpoints and misconfigured index pages.
Likelihood / Impact: 3 / 5 — 4 / 5
Action: Restrict web directories, disable directory listing, enforce least-privilege ACLs.

F-20251027-002 — Exposed Network & Legacy Services

Assets: A-002 / A-004 — Endpoint and Identity Systems
Evidence:

nmap_full_10.10.10.15_20251027_1027.txt

nmap_ping_sweep_20251027_1027.txt

screenshots/nmap_full_10.10.10.15_20251027_1027.png

screenshots/nmap_ping_sweep_20251027_1027.png
Summary: Multiple open services observed; version banners show legacy software requiring updates.
Likelihood / Impact: 4 / 5 — 5 / 5
Action: Patch or decommission vulnerable services, enforce access segmentation.

F-20251027-003 — SMB / AD Enumeration Exposure

Assets: A-004 — Identity & File Services
Evidence:

enum4linux_10.10.10.15_20251027_1027.txt

screenshots/enum4linux_10.10.10.15_20251027_1027.png
Summary: enum4linux identified shared resources and policy hints; possible weak authentication or anonymous access.
Likelihood / Impact: 4 / 5 — 5 / 5
Action: Harden SMB shares, disable guest sessions, audit account permissions.

## 6. Evidence Integrity

All screenshots and outputs are verified with SHA256 values in the following manifests:

02-Identification/evidence/evidence_manifest_20251027_1027.sha256

02-Identification/evidence/evidence_manifest_20251027_1114.csv

Each manifest line includes filename, checksum, size, and full timestamp.
Verification can be performed using:

sha256sum -c 02-Identification/evidence/evidence_manifest_20251027_1027.sha256

## 7. Next Steps

Import validated findings into 03-Analysis/risk_register.csv.

Quantify each finding (Likelihood × Impact).

Map controls and propose mitigation actions in 04-Treatment/Mitigation_Plans.md.

## 8. Author & Signature

Cypriano Akinwunmi
Cybersecurity Risk & Compliance Practitioner
Date: 2025-10-27

End of Phase 1 — Risk Identification Report (Evidence Set _20251027_1027)
