
# 02 – Risk Identification Report

*Enterprise Cybersecurity Risk Management Framework (ISO 31000 / NIST RMF)*  
**Date:** October 30, 2025  
**Author:** Cypriano Akinwunmi
  

---

## **Objective**
This phase focuses on identifying and documenting potential cybersecurity risks by performing reconnaissance and enumeration of the target environment. Each activity generates evidence files and screenshots to ensure traceability and accountability.

---

## **Tools and Utilities Used**
| Tool | Purpose |
|------|----------|
| `nmap` | Host discovery and service enumeration |
| `nikto` | Web vulnerability scanning |
| `gobuster` | Directory enumeration |
| `enum4linux` | SMB/NetBIOS enumeration |
| `scrot` | Screenshot evidence capture |
| `sha256sum` | Evidence integrity verification |

---

## **Execution Summary**
All scans were performed against the target **10.10.10.15** during the identification phase.  
The timestamps below correspond to actual evidence and screenshots stored in the repository.

---

### **1. Network Host Discovery**

```bash
nmap -sn 10.10.10.0/24 -oN 02-Identification/evidence/nmap_ping_sweep_20251030_0447.txt

##  Observation:
Nmap discovered one active host at 10.10.10.7. The remaining hosts in the subnet were not responsive, possibly due to firewall filtering or offline status.

---

### **2. Full TCP and Service Scan

```bash
nmap -sS -sV -O -p- -T4 10.10.10.15 -oN 02-Identification/evidence/nmap_full_10.10.10.15_20251030_0448.txt

## Observation:
The target host did not respond to port or service probes. It may be blocking ICMP or running behind a firewall that filters external scans.

---

### **3. Web Vulnerability Assessment

```bash
nikto -host http://10.10.10.15 -o 02-Identification/evidence/nikto_10.10.10.15_20251030_0449.txt

## Observation:
No active web service was detected on the target host. Nikto was unable to complete any vulnerability tests.

---

### **4. Directory Enumeration

```bash
gobuster dir -u http://10.10.10.15 -w /usr/share/wordlists/dirb/common.txt -o 02-Identification/evidence/gobuster_10.10.10.15_20251030_0450.txt

## Observation:
Gobuster failed to connect to the target’s web server. No directories or files were enumerated successfully.

---

### **5. SMB/NetBIOS Enumeration

```bash
enum4linux -a 10.10.10.15 | tee 02-Identification/evidence/enum4linux_10.10.10.15_20251030_0452.txt

## Observation:
No domain or share information was available. SMB sessions were not permitted with null credentials. The host refused anonymous enumeration.

---

### Summary of Risk Indicators

| Category               | Indicator                           | Risk Identified                                            |
| ---------------------- | ----------------------------------- | ---------------------------------------------------------- |
| Network Availability   | Host intermittently unreachable     | Possible firewall or intrusion prevention filtering        |
| Service Exposure       | Web and SMB services non-responsive | Low external exposure but limited visibility for defenders |
| Information Disclosure | Enumeration attempts blocked        | Good defensive posture observed                            |
| Audit Integrity        | SHA256 manifest maintained          | Provides assurance of evidence authenticity                |


## Tools used
`nmap`, `nikto`, `gobuster`, `enum4linux`, `scrot` (screenshots), `sha256sum`

---

## Evidence (selected set created on 2025-10-30)

### Raw evidence files (stored in `02-Identification/evidence/`)
- `02-Identification/evidence/nmap_ping_sweep_20251030_0447.txt`  
  - **Size:** (see manifest) — **Timestamp:** 2025-10-30 04:47 EDT

- `02-Identification/evidence/nmap_full_10.10.10.15_20251030_0448.txt`  
  - **Size:** (see manifest) — **Timestamp:** 2025-10-30 04:48 EDT

- `02-Identification/evidence/nikto_10.10.10.15_20251030_0449.txt`  
  - **Size:** (see manifest) — **Timestamp:** 2025-10-30 04:49 EDT

- `02-Identification/evidence/gobuster_10.10.10.15_20251030_0450.txt`  
  - **Size:** (see manifest) — **Timestamp:** 2025-10-30 04:50 EDT

- `02-Identification/evidence/enum4linux_10.10.10.15_20251030_0452.txt`  
  - **Size:** (see manifest) — **Timestamp:** 2025-10-30 04:52 EDT

### Evidence manifest files
- `02-Identification/evidence/evidence_manifest_20251030_0452.sha256` — **Timestamp:** 2025-10-30 04:52 EDT  
- (Optional CSV manifest if present): `02-Identification/evidence/evidence_manifest_20251030_1114.csv` — **Timestamp:** 2025-10-27 11:14:09 (if present)

---

## Screenshots (stored in `screenshots/`) — **visible on GitHub**

(These lines use relative paths from this file location `02-Identification/` → `../screenshots/`)

### Nmap — ping sweep (2025-10-30 04:47 EDT)  
![](../screenshots/nmap_ping_sweep_20251030_0447.png)

### Nmap — full service enumeration (2025-10-30 04:48 EDT)  
![](../screenshots/nmap_full_10.10.10.15_20251030_0448.png)

### Nikto — HTTP checks (2025-10-30 04:49 EDT)  
![](../screenshots/nikto_10.10.10.15_20251030_0449.png)

### Gobuster — directory enumeration (2025-10-30 04:50 EDT)  
![](../screenshots/gobuster_10.10.10.15_20251030_0450.png)

### Enum4linux — SMB / AD enumeration (2025-10-30 04:52 EDT)  
![](../screenshots/enum4linux_10.10.10.15_20251030_0452.png)

---

## Commands executed (exact - outputs saved to the filenames above)

```bash
nmap -sn 10.10.10.0/24 -oN 02-Identification/evidence/nmap_ping_sweep_20251030_0447.txt
nmap -sS -sV -O -p- -T4 10.10.10.15 -oN 02-Identification/evidence/nmap_full_10.10.10.15_20251030_0448.txt
nikto -host http://10.10.10.15 -o 02-Identification/evidence/nikto_10.10.10.15_20251030_0449.txt
gobuster dir -u http://10.10.10.15 -w /usr/share/wordlists/dirb/common.txt -o 02-Identification/evidence/gobuster_10.10.10.15_20251030_0450.txt
enum4linux -a 10.10.10.15 | tee 02-Identification/evidence/enum4linux_10.10.10.15_20251030_0452.txt
sha256sum 02-Identification/evidence/* > 02-Identification/evidence/evidence_manifest_20251030_0452.sha256
```
### Conclusion

The identification phase achieved its primary goal of mapping reachable systems and evaluating initial exposure. Although most scans revealed restricted access, these results confirm that defensive measures (such as firewall rules and service hardening) are in place.

All findings, evidence, and screenshots are stored under:

02-Identification/evidence/

02-Identification/screenshots/

These artifacts are validated by the SHA256 manifest for traceability and compliance review.

---

### 👤 Author

**Cypriano Akinwunmi**  
Cybersecurity GRC & Risk Management Professional  
GitHub: [@cykins4good](https://github.com/cykins4good)  
LinkedIn: [linkedin.com/in/cypriano-akinwunmi](https://www.linkedin.com/in/cypriano-akinwunmi-33383063/)
